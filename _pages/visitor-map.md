---
permalink: /visitor-map/
title: "Visitor Map"
author_profile: true
---

{% assign vm = site.visitor_map %}

{% if vm.provider == "clustrmaps" and vm.clustrmaps_d and vm.clustrmaps_d != "" %}
<h2>{{ vm.title | default: "Where Visitors Come From" }}</h2>
<p>This map is powered by ClustrMaps and updates as visits are recorded.</p>

<div style="max-width: 820px; margin: 1rem auto;">
  {% if vm.widget == "map_v2" %}
  <script
    type="text/javascript"
    id="clustrmaps"
    src="//clustrmaps.com/map_v2.js?d={{ vm.clustrmaps_d }}&cl={{ vm.map_text_color | default: 'ffffff' }}&w={{ vm.map_width | default: 'a' }}">
  </script>
  {% else %}
  <script
    type="text/javascript"
    id="clstr_globe"
    src="//clustrmaps.com/globe.js?d={{ vm.clustrmaps_d }}">
  </script>
  {% endif %}
</div>

<p style="font-size: 0.9em; opacity: 0.8;">
  Note: Geo-location is approximate and usually resolved at city/country level.
</p>
{% else %}
<h2>Visitor Map Setup Required</h2>
<p>To enable this map, set <code>visitor_map.clustrmaps_d</code> in <code>_config.yml</code>.</p>

<ol>
  <li>Go to <a href="https://clustrmaps.com/" target="_blank" rel="noopener">ClustrMaps</a> and register your website.</li>
  <li>Find the script key value used in their widget URL parameter <code>d=...</code>.</li>
  <li>Paste that value into <code>visitor_map.clustrmaps_d</code> in <code>_config.yml</code>.</li>
  <li>Redeploy your site.</li>
</ol>
{% endif %}
