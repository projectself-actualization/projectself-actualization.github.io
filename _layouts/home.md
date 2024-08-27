---
# Mr. Green Jekyll Theme (https://github.com/MrGreensWorkshop/MrGreen-JekyllTheme)
# Copyright (c) 2022 Mr. Green's Workshop https://www.MrGreensWorkshop.com
# Licensed under MIT

layout: default
# main page (index.html)
---
{%- include multi_lng/get-pages-by-lng.liquid pages = site.posts -%}

{%- if page.img %}
  {%- if site.data.conf.others.home.header_img_with_img_tag == true -%}
    {%- capture home_img_tag -%} <img src="{{ page.img }}" /> {%- endcapture -%}
    {%- capture home_img_background_style -%} style="height: unset;" {%- endcapture -%}
  {% else %}
    {%- capture home_img_background_style -%} style="background-image:url('{{ page.img }}');" {%- endcapture -%}
  {%- endif -%}
{%- endif -%}

<div class="multipurpose-container home-heading-container">
  <div class="home-heading" {{ home_img_background_style }}>
    {{ home_img_tag }}
    <div class="home-heading-message">
      {{ site.data.owner[lng].home.top_header_line1
        | replace: site.data.conf.main.brand_replace, site.data.owner[lng].brand
        | replace: site.data.conf.main.greetings_replace, site.data.lang[lng].constants.greetings
        | replace: site.data.conf.main.welcome_replace, site.data.lang[lng].constants.welcome }}
      {%- if site.data.owner[lng].home.top_header_line2 %}
        <br>
        {{ site.data.owner[lng].home.top_header_line2
          | replace: site.data.conf.main.brand_replace, site.data.owner[lng].brand
          | replace: site.data.conf.main.greetings_replace, site.data.lang[lng].constants.greetings
          | replace: site.data.conf.main.welcome_replace, site.data.lang[lng].constants.welcome }}
      {% endif -%}
    </div>
  </div>
  <div class="home-intro-text markdown-style">
    {{ content }}
  </div>
</div>
