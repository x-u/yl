
cd /Users/titanic/Dropbox/3Res_Others/Website/yanlongindustrial
jekyll serve --livereload --open-url

<!-- If Condition -->
{% if page.lang=="zh" %}
	{{site.title}}
{% else %}
	{{site.title-en}}
{% endif %}

<!-- Filter -->
{% assign filtered_companies = site.companies | where: 'lang', page.lang %}
{% assign filtered_companies = filtered_companies | where: 'mainpage', true %}
{% assign weighted_companies = filtered_companies | sort: "weight" %}
{% for company in weighted_companies %}
{% endfor %}

<!-- Alternatively -->
{% for post in site.companies %}
  {% if post.company==page.company and post.mainpage==false and post.lang==page.lang %}
    <li>
      <h2><a href="{{ post.url | absolute_url }}">{{ post.title }}</a></h2>
      {{ post.excerpt }}
    </li>
  {% endif %}
{% endfor %}
