---
layout: page
name: "Blog"
group: navigation
title: "Blog"
permalink: "blog.html"
---
{% include JB/setup %}

<ul class="nav nav-tabs">
	<li class="active"><a href="#latest-posts" data-toggle="tab">Latest Posts </a></li>
	<li><a href="#tags" data-toggle="tab">Tags </a></li>
	<li><a href="#categories" data-toggle="tab">Categories </a></li>
	<li><a href="#archive" data-toggle="tab">Archive </a></li>
</ul>
<div class="tabbable">
	<div class="tab-content">
		<div class="tab-pane active" id="latest-posts">
			<p>
				<h4> Blog Roll </h4>
				<ul class="posts">
					{% for post in site.posts %}
					<li>
						<span>{{ post.date | date_to_string }}</span> &raquo; <a href="{{ BASE_PATH }}{{ post.url }}">{{ post.title }}</a>
						<p>{{ post.description }}</p>
					</li>
					<hr>
					{% endfor %}
				</ul>
			</p>
		</div>
		<div class="tab-pane" id="tags">
			<p>
				<div>
					<ul class="tag_box inline">
						{% assign tags_list = site.tags %}  
						{% include JB/tags_list %}
					</ul>
					<hr/>
					<div class="well" style="padding: 8px 0;">
						<ul class="nav nav-list">
							{% for tag in site.tags %}
							<li class="nav-header" id="{{ tag[0] }}-ref">{{ tag[0] }}</li>
							{% assign pages_list = tag[1] %}  
							{% include JB/pages_list %}
							{% endfor %}
						</ul>
					</div>
				</div>
			</p>
		</div>
		<div class="tab-pane" id="categories">
			<p>
				<div>
					<ul class="tag_box inline">
						{% assign categories_list = site.categories %}
						{% include JB/categories_list %}
					</ul>
					<hr/>
					<div class="well" style="padding: 8px 0;">
						<ul class="nav nav-list">
							{% for category in site.categories %} 
							<li class="nav-header" id="{{ category[0] }}-ref">{{ category[0] | join: "/" }}</li>
							{% assign pages_list = category[1] %}  
							{% include JB/pages_list %}
							{% endfor %}
						</ul>
					</div>
				</div>
			</p>
		</div>
		<div class="tab-pane" id="archive">
			<p>
				{% assign posts_collate = site.posts %}
				{% include JB/posts_collate %}
			</p>
		</div>
	</div>
</div>
