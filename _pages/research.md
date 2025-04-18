---
title: Research
permalink: assets/research/
layout: splash
---

<div class="card">

  {% assign datasets = "publications-working" | split: ", " %}
  
  {% for ds in datasets %}
  
    <div class="jumbotron text-center">
      <h2>
      {% if ds == 'publications' %} Publications {% endif %}
	  {% if ds == 'publications-working' %} Working papers {% endif %}
	  {% if ds == 'publications-chapters' %} Book chapters {% endif %}
	  {% if ds == 'publications-other' %} Other publications{% endif %}
	  </h2>
    </div>
    
    {% for item in site.data[ds] %}
    
      <div class="card-body">
        <p class="card-text">
	  	<b>{{ item.title }} </b><br>
	  	  
	  	{% if item.coauthors != blank %} with {{ item.coauthors }} <br> {% endif %}
	  	  
	  	{% if item.publication != blank %} {{ item.publication | replace_first: '*', '<span style="color:FireBrick"><em>' | replace_first: '*', '</em></span>' }} <br>  {% endif %}
	  	
	  	{% if item.award != blank %} {{ item.award | markdownify | remove:'<p>' | remove:'</p>'}} <br>  {% endif %}
    
	  	{% for m in item.media %}
	  	  {% if forloop.first %} Media: {% endif %}
	  	  {% if forloop.last %} {{ m | markdownify | remove:'<p>' | remove:'</p>'}} <br> 
	  	  {% else %} {{ m | markdownify | remove:'<p>' | remove:'</p>' | rstrip | append: ', '}}
	  	  {% endif %}	
	  	{% endfor %}
    
	  	{% for p in item.policy %}
	  	  {% if forloop.first %} Policy: {% endif %}
	  	  {% if forloop.last %} {{ p | markdownify | remove:'<p>' | remove:'</p>'}} <br> 
	  	  {% else %} {{ p | markdownify | remove:'<p>' | remove:'</p>' | rstrip | append: ', '}}
	  	  {% endif %}	
	  	{% endfor %}		
    
	  	{% for o in item.other %}
	  	  {{ o | markdownify | remove:'<p>' | remove:'</p>'}}
	  	  {% if forloop.last %} <br> 
	  	  {% else %} |
	  	  {% endif %}		  
	  	{% endfor %}		  
    
	  	{% if item.abstract != blank %}
	  	  <details>
	  		<summary style="margin-top: -1.3em; ">Abstract</summary>
	  		<p class="notice" style="margin-top:0 !important">{{ item.abstract }}</p>
	  	  </details>
	  	{% endif %}
	    </p>
      </div>
    {% endfor %}
  
  {% endfor %}
  

  {% endfor %}
  
</div>


