---
title: "Punbb php not shown from outside"
date: 2011-07-14
forum: General Help
---

### Post by gypsumwolf on 2011-07-14
I am running [PunBB]("http://punbb.informer.com/") on my home server (Lubuntu). It works fine while browsing the site from my desktop computer via internal IP. When I access the domain name from outside my router it does not display the site correctly, instead of a nice php site, it pulls up a site that looks like no php was used.

If I try and access a index.html page (instead of the index.php) on my server from the outside it works real quick with no problems.

Using pot 80.

---

### Post by mikejonesey on 2011-07-14
> **gypsumwolf said:**
> I am running [PunBB]("http://punbb.informer.com/") on my home server (Lubuntu). It works fine while browsing the site from my desktop computer via internal IP. When I access the domain name from outside my router it does not display the site correctly, instead of a nice php site, it pulls up a site that looks like no php was used.

If I try and access a index.html page (instead of the index.php) on my server from the outside it works real quick with no problems.

Using pot 80.

can you attatch source internal and external please...

---

### Post by gypsumwolf on 2011-07-14
Source of what?

Internal website source:
```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en" dir="ltr">
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta name="description" content="Eon - A discussion of times past, with the future in mind." />
<title>Eon</title>
<link rel="alternate" type="application/rss+xml" href="http://10.0.0.3/forums/extern.php?action=feed&amp;type=rss" title="RSS" />
<link rel="alternate" type="application/atom+xml" href="http://10.0.0.3/forums/extern.php?action=feed&amp;type=atom" title="ATOM" />
<link rel="top" href="http://10.0.0.3/forums" title="Forum index" />
<link rel="search" href="http://10.0.0.3/forums/search.php" title="Search" />
<link rel="author" href="http://10.0.0.3/forums/userlist.php" title="User list" />
<link rel="stylesheet" type="text/css" media="screen" href="http://10.0.0.3/forums/style/Oxygen/Oxygen.css" />
<link rel="stylesheet" type="text/css" media="screen" href="http://10.0.0.3/forums/style/Oxygen/Oxygen_cs.css" />
<!--[if lte IE 6]><link rel="stylesheet" type="text/css" href="http://10.0.0.3/forums/style/Oxygen/Oxygen_ie6.css" /><![endif]-->
<!--[if IE 7]><link rel="stylesheet" type="text/css" href="http://10.0.0.3/forums/style/Oxygen/Oxygen_ie7.css" /><![endif]-->

<!--[if IE 8]><link rel="stylesheet" type="text/css" href="http://10.0.0.3/forums/style/Oxygen/Oxygen_ie8.css" /><![endif]-->
<script type="text/javascript" src="http://10.0.0.3/forums/include/js/common.js"></script>
</head>
<body>

<div id="brd-wrap" class="brd">
<div id="brd-index" class="brd-page basic-page">

<div id="brd-head" class="gen-content">
	<p id="brd-access"><a href="#brd-main">Skip to forum content</a></p>
	<p id="brd-title"><a href="http://10.0.0.3/forums/index.php">Eon</a></p>
	<p id="brd-desc">A discussion of times past, with the future in mind.</p>

</div>

<div id="brd-navlinks" class="gen-content">
	<ul>
		<li id="navindex" class="isactive"><a href="http://10.0.0.3/forums/index.php">Index</a></li>
		<li id="navuserlist"><a href="http://10.0.0.3/forums/userlist.php">User list</a></li>
		<li id="navsearch"><a href="http://10.0.0.3/forums/search.php">Search</a></li>
		<li id="navregister"><a href="http://10.0.0.3/forums/register.php">Register</a></li>

		<li id="navlogin"><a href="http://10.0.0.3/forums/login.php">Login</a></li>
	</ul>
	
</div>

<div id="brd-visit" class="gen-content">
	<p id="welcome"><span>You are not logged in.</span> <span>Please login or register.</span></p>
	<p id="visit-links" class="options"><span id="visit-recent" class="first-item"><a href="http://10.0.0.3/forums/search.php?action=show_recent" title="Find topics which contain recent posts.">Active topics</a></span> <span id="visit-unanswered"><a href="http://10.0.0.3/forums/search.php?action=show_unanswered" title="Find topics which have not been replied to.">Unanswered topics</a></span></p>

</div>



<div class="hr"><hr /></div>

<div id="brd-main">
	<h1 class="main-title">Eon</h1>

	
	
	
	<div class="main-head">
		<h2 class="hn"><span>Main Discussion</span></h2>
	</div>

	<div class="main-subhead">
		<p class="item-summary"><span><strong class="subject-title">Forums</strong> in this category with details of <strong class="info-topics">topics</strong>, <strong class="info-posts">posts</strong>, <strong class="info-lastpost">last post</strong></span></p>
	</div>
	<div id="category1" class="main-content main-category">
		<div id="forum2" class="main-item odd main-first-item">

			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=2"><span>General</span></a></h3>
				<p>This is for any discussion that does not fall under any of the other topics.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>1</strong> <span class="label">topic</span></li>

				<li class="info-posts"><strong>1</strong> <span class="label">post</span></li>
				<li class="info-lastpost"><span class="label">Last post:</span> <strong><a href="http://10.0.0.3/forums/viewtopic.php?pid=2#p2">2011-07-09 21:51:28</a></strong> <cite>by wolf</cite></li>
			</ul>
		</div>
		<div id="forum12" class="main-item even">

			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=12"><span>Antediluvian</span></a></h3>
				<p>The period of time between Creation and The Flood.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>

				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>
		<div id="forum22" class="main-item odd">
			<span class="icon "><!-- --></span>
			<div class="item-subject">

				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=22"><span>Flood</span></a></h3>
				<p>The famous Biblical Flood, also known as the Deluge.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>

				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>
		<div id="forum26" class="main-item even">
			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=26"><span>Evolution</span></a></h3>
				<p>The belief/theory which Charles Darwin is largely considered the founder of.</p>

			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>

			</ul>
		</div>
		<div id="forum24" class="main-item odd">
			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=24"><span>Astronomy</span></a></h3>
				<p>The study of the expanse and everything in it that is not considered part of the Earth.</p>
			</div>

			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>

		</div>
		<div id="forum23" class="main-item even">
			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=23"><span>Geology</span></a></h3>
				<p>Rocks, Minerals and the physical foundations of the Earth.</p>
			</div>
			<ul class="item-info">

				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>

		<div id="forum7" class="main-item odd">
			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=7"><span>Civilisations</span></a></h3>
				<p>Study of the development of Civilisations and Governments.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>1</strong> <span class="label">topic</span></li>

				<li class="info-posts"><strong>1</strong> <span class="label">post</span></li>
				<li class="info-lastpost"><span class="label">Last post:</span> <strong><a href="http://10.0.0.3/forums/viewtopic.php?pid=7#p7">2011-07-10 17:23:38</a></strong> <cite>by wolf</cite></li>
			</ul>
		</div>
		<div id="forum27" class="main-item even">

			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=27"><span>Philosophy</span></a></h3>
				<p>Reason, Knowledge, Ethics, Wisdom and The Mind.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>

				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>
		<div id="forum25" class="main-item odd">
			<span class="icon "><!-- --></span>
			<div class="item-subject">

				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=25"><span>Library</span></a></h3>
				<p>If you know a book, writing, or anything of that sort which you would like to store in our library.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>

				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>
	</div>
	<div class="main-head">
		<h2 class="hn"><span>Forum Technical Support</span></h2>
	</div>
	<div class="main-subhead">

		<p class="item-summary"><span><strong class="subject-title">Forums</strong> in this category with details of <strong class="info-topics">topics</strong>, <strong class="info-posts">posts</strong>, <strong class="info-lastpost">last post</strong></span></p>
	</div>
	<div id="category2" class="main-content main-category">
		<div id="forum6" class="main-item odd main-first-item">
			<span class="icon "><!-- --></span>

			<div class="item-subject">
				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=6"><span>Help</span></a></h3>
				<p>Not sure what to do, or the website is not working properly?</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>1</strong> <span class="label">topic</span></li>

				<li class="info-posts"><strong>1</strong> <span class="label">post</span></li>
				<li class="info-lastpost"><span class="label">Last post:</span> <strong><a href="http://10.0.0.3/forums/viewtopic.php?pid=3#p3">2011-07-10 09:32:26</a></strong> <cite>by wolf</cite></li>
			</ul>
		</div>
		<div id="forum18" class="main-item even">

			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://10.0.0.3/forums/viewforum.php?id=18"><span>Suggestions</span></a></h3>
				<p>Got a better idea?</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>1</strong> <span class="label">topic</span></li>

				<li class="info-posts"><strong>1</strong> <span class="label">post</span></li>
				<li class="info-lastpost"><span class="label">Last post:</span> <strong><a href="http://10.0.0.3/forums/viewtopic.php?pid=4#p4">2011-07-10 09:58:46</a></strong> <cite>by wolf</cite></li>
			</ul>
		</div>
	</div>

	
	
</div>
<!-- forum_qpost -->

<div id="brd-stats" class="gen-content">
	<h2 class="hn"><span>Forum statistics</span></h2>
	<ul>
		<li class="st-users"><span>Total number of registered users: <strong>1</strong></span></li>
		<li class="st-users"><span>Newest registered user: <strong><a href="http://10.0.0.3/forums/profile.php?id=2">wolf</a></strong></span></li>

		<li class="st-activity"><span>Total number of topics: <strong>4</strong></span></li>
		<li class="st-activity"><span>Total number of posts: <strong>4</strong></span></li>
	</ul>
</div>
<div id="brd-online" class="gen-content">
	<h3 class="hn"><span>Currently online ( <strong>2</strong> guests, <strong>0</strong> registered users )</span></h3>

</div>

<div class="hr"><hr /></div>

<div id="brd-about" class="gen-content">
	<form id="qjump" method="get" accept-charset="utf-8" action="http://10.0.0.3/forums/viewforum.php">
	<div class="frm-fld frm-select">
		<label for="qjump-select"><span>Jump to forum:</span></label><br />
		<span class="frm-input"><select id="qjump-select" name="id">
			<optgroup label="Main Discussion">
				<option value="2">General</option>

				<option value="12">Antediluvian</option>
				<option value="22">Flood</option>
				<option value="26">Evolution</option>
				<option value="24">Astronomy</option>
				<option value="23">Geology</option>
				<option value="7">Civilisations</option>

				<option value="27">Philosophy</option>
				<option value="25">Library</option>
			</optgroup>
			<optgroup label="Forum Technical Support">
				<option value="6">Help</option>
				<option value="18">Suggestions</option>
			</optgroup>

		</select>
		<input type="submit" value="Go" onclick="return Forum.doQuickjumpRedirect(forum_quickjump_url, sef_friendly_url_array);" /></span>
	</div>
</form>
<script type="text/javascript">
		var forum_quickjump_url = "http://10.0.0.3/forums/viewforum.php?id=$1";
		var sef_friendly_url_array = new Array(11);
	sef_friendly_url_array[2] = "general";
	sef_friendly_url_array[12] = "antediluvian";
	sef_friendly_url_array[22] = "flood";
	sef_friendly_url_array[26] = "evolution";
	sef_friendly_url_array[24] = "astronomy";
	sef_friendly_url_array[23] = "geology";
	sef_friendly_url_array[7] = "civilisations";
	sef_friendly_url_array[27] = "philosophy";
	sef_friendly_url_array[25] = "library";
	sef_friendly_url_array[6] = "help";
	sef_friendly_url_array[18] = "suggestions";
</script>
	<p id="copyright">Powered by <strong><a href="http://punbb.informer.com/">PunBB</a></strong>, supported by <strong><a href="http://www.informer.com/">Informer Technologies, Inc</a></strong>.</p>
<p style="clear: both; ">The pun_repository official extension is installed. Copyright &copy; 2003&ndash;2009 <a href="http://punbb.informer.com/">PunBB</a>.</p>

</div>

<!-- forum_debug -->

</div>
</div>

</body>
</html>

```

External website source:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">

<html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en" dir="ltr">
<head>   <script type="text/javascript">ginf={url:'http://zend2.com',script:'Def.php',target:{h:'http://ancienteon.com',p:'/forums/',b:''},enc:{u:'',e:'1',p:''},b:'5'}</script>
   <script type="text/javascript" src="http://zend2.com/includes/main.js"></script>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8" />
<meta name="description" content="Eon - A discussion of times past, with the future in mind." />
<title>Eon</title>
<link rel="alternate" type="application/rss+xml" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL2V4dGVybi5waHA%2FYWN0aW9uPWZlZWQmdHlwZT1yc3M%3D&amp;b=5" title="RSS" />
<link rel="alternate" type="application/atom+xml" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL2V4dGVybi5waHA%2FYWN0aW9uPWZlZWQmdHlwZT1hdG9t&amp;b=5" title="ATOM" />
<link rel="top" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1z&amp;b=5" title="Forum index" />
<link rel="search" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3NlYXJjaC5waHA%3D&amp;b=5" title="Search" />

<link rel="author" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3VzZXJsaXN0LnBocA%3D%3D&amp;b=5" title="User list" />
<link rel="stylesheet" type="text/css" media="screen" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3N0eWxlL094eWdlbi9PeHlnZW4uY3Nz&amp;b=5" />
<link rel="stylesheet" type="text/css" media="screen" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3N0eWxlL094eWdlbi9PeHlnZW5fY3MuY3Nz&amp;b=5" />
<!--[if lte IE 6]><link rel="stylesheet" type="text/css" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3N0eWxlL094eWdlbi9PeHlnZW5faWU2LmNzcw%3D%3D&amp;b=5" /><![endif]-->
<!--[if IE 7]><link rel="stylesheet" type="text/css" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3N0eWxlL094eWdlbi9PeHlnZW5faWU3LmNzcw%3D%3D&amp;b=5" /><![endif]-->
<!--[if IE 8]><link rel="stylesheet" type="text/css" href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3N0eWxlL094eWdlbi9PeHlnZW5faWU4LmNzcw%3D%3D&amp;b=5" /><![endif]-->
<script type="text/javascript" src="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL2luY2x1ZGUvanMvY29tbW9uLmpz&amp;b=5"></script>
</head>
<body><div>
  <div align="center"><a href="index.php">Proxy Home</a></div>
  <div align="center"><br />

<script type="text/javascript" src="http://www.cpalead.com/mygateway.php?pub=66609&amp;gateid=MTMzNjg2"></script>

</div>


<div id="brd-wrap" class="brd">
<div id="brd-index" class="brd-page basic-page">

<div id="brd-head" class="gen-content">
	<p id="brd-access"><a href="">Skip to forum content</a></p>
	<p id="brd-title"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL2luZGV4LnBocA%3D%3D&amp;b=5">Eon</a></p>
	<p id="brd-desc">A discussion of times past, with the future in mind.</p>
</div>

<div id="brd-navlinks" class="gen-content">
	<ul>
		<li id="navindex" class="isactive"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL2luZGV4LnBocA%3D%3D&amp;b=5">Index</a></li>
		<li id="navuserlist"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3VzZXJsaXN0LnBocA%3D%3D&amp;b=5">User list</a></li>
		<li id="navsearch"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3NlYXJjaC5waHA%3D&amp;b=5">Search</a></li>
		<li id="navregister"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3JlZ2lzdGVyLnBocA%3D%3D&amp;b=5">Register</a></li>
		<li id="navlogin"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL2xvZ2luLnBocA%3D%3D&amp;b=5">Login</a></li>

	</ul>
	
</div>

<div id="brd-visit" class="gen-content">
	<p id="welcome"><span>You are not logged in.</span> <span>Please login or register.</span></p>
	<p id="visit-links" class="options"><span id="visit-recent" class="first-item"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3NlYXJjaC5waHA%2FYWN0aW9uPXNob3dfcmVjZW50&amp;b=5" title="Find topics which contain recent posts.">Active topics</a></span> <span id="visit-unanswered"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3NlYXJjaC5waHA%2FYWN0aW9uPXNob3dfdW5hbnN3ZXJlZA%3D%3D&amp;b=5" title="Find topics which have not been replied to.">Unanswered topics</a></span></p>
</div>



<div class="hr"><hr /></div>

<div id="brd-main">
	<h1 class="main-title">Eon</h1>

	
	
	
	<div class="main-head">
		<h2 class="hn"><span>Main Discussion</span></h2>
	</div>

	<div class="main-subhead">
		<p class="item-summary"><span><strong class="subject-title">Forums</strong> in this category with details of <strong class="info-topics">topics</strong>, <strong class="info-posts">posts</strong>, <strong class="info-lastpost">last post</strong></span></p>
	</div>
	<div id="category1" class="main-content main-category">
		<div id="forum2" class="main-item odd main-first-item">

			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9Mg%3D%3D&amp;b=5"><span>General</span></a></h3>
				<p>This is for any discussion that does not fall under any of the other topics.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>1</strong> <span class="label">topic</span></li>

				<li class="info-posts"><strong>1</strong> <span class="label">post</span></li>
				<li class="info-lastpost"><span class="label">Last post:</span> <strong><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXd0b3BpYy5waHA%2FcGlkPQ%3D%3D&amp;b=5#p2">2011-07-09 21:51:28</a></strong> <cite>by wolf</cite></li>
			</ul>
		</div>
		<div id="forum12" class="main-item even">

			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9MTI%3D&amp;b=5"><span>Antediluvian</span></a></h3>
				<p>The period of time between Creation and The Flood.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>

				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>
		<div id="forum22" class="main-item odd">
			<span class="icon "><!-- --></span>
			<div class="item-subject">

				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9MjI%3D&amp;b=5"><span>Flood</span></a></h3>
				<p>The famous Biblical Flood, also known as the Deluge.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>

				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>
		<div id="forum26" class="main-item even">
			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9MjY%3D&amp;b=5"><span>Evolution</span></a></h3>
				<p>The belief/theory which Charles Darwin is largely considered the founder of.</p>

			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>

			</ul>
		</div>
		<div id="forum24" class="main-item odd">
			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9MjQ%3D&amp;b=5"><span>Astronomy</span></a></h3>
				<p>The study of the expanse and everything in it that is not considered part of the Earth.</p>
			</div>

			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>

		</div>
		<div id="forum23" class="main-item even">
			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9MjM%3D&amp;b=5"><span>Geology</span></a></h3>
				<p>Rocks, Minerals and the physical foundations of the Earth.</p>
			</div>
			<ul class="item-info">

				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>

		<div id="forum7" class="main-item odd">
			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9Nw%3D%3D&amp;b=5"><span>Civilisations</span></a></h3>
				<p>Study of the development of Civilisations and Governments.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>1</strong> <span class="label">topic</span></li>

				<li class="info-posts"><strong>1</strong> <span class="label">post</span></li>
				<li class="info-lastpost"><span class="label">Last post:</span> <strong><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXd0b3BpYy5waHA%2FcGlkPQ%3D%3D&amp;b=5#p7">2011-07-10 17:23:38</a></strong> <cite>by wolf</cite></li>
			</ul>
		</div>
		<div id="forum27" class="main-item even">

			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9Mjc%3D&amp;b=5"><span>Philosophy</span></a></h3>
				<p>Reason, Knowledge, Ethics, Wisdom and The Mind.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>

				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>
				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>
		<div id="forum25" class="main-item odd">
			<span class="icon "><!-- --></span>
			<div class="item-subject">

				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9MjU%3D&amp;b=5"><span>Library</span></a></h3>
				<p>If you know a book, writing, or anything of that sort which you would like to store in our library.</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>0</strong> <span class="label">topics</span></li>
				<li class="info-posts"><strong>0</strong> <span class="label">posts</span></li>

				<li class="info-lastpost"><strong>Never</strong></li>
			</ul>
		</div>
	</div>
	<div class="main-head">
		<h2 class="hn"><span>Forum Technical Support</span></h2>
	</div>
	<div class="main-subhead">

		<p class="item-summary"><span><strong class="subject-title">Forums</strong> in this category with details of <strong class="info-topics">topics</strong>, <strong class="info-posts">posts</strong>, <strong class="info-lastpost">last post</strong></span></p>
	</div>
	<div id="category2" class="main-content main-category">
		<div id="forum6" class="main-item odd main-first-item">
			<span class="icon "><!-- --></span>

			<div class="item-subject">
				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9Ng%3D%3D&amp;b=5"><span>Help</span></a></h3>
				<p>Not sure what to do, or the website is not working properly?</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>1</strong> <span class="label">topic</span></li>

				<li class="info-posts"><strong>1</strong> <span class="label">post</span></li>
				<li class="info-lastpost"><span class="label">Last post:</span> <strong><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXd0b3BpYy5waHA%2FcGlkPQ%3D%3D&amp;b=5#p3">2011-07-10 09:32:26</a></strong> <cite>by wolf</cite></li>
			</ul>
		</div>
		<div id="forum18" class="main-item even">

			<span class="icon "><!-- --></span>
			<div class="item-subject">
				<h3 class="hn"><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%2FaWQ9MTg%3D&amp;b=5"><span>Suggestions</span></a></h3>
				<p>Got a better idea?</p>
			</div>
			<ul class="item-info">
				<li class="info-topics"><strong>1</strong> <span class="label">topic</span></li>

				<li class="info-posts"><strong>1</strong> <span class="label">post</span></li>
				<li class="info-lastpost"><span class="label">Last post:</span> <strong><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXd0b3BpYy5waHA%2FcGlkPQ%3D%3D&amp;b=5#p4">2011-07-10 09:58:46</a></strong> <cite>by wolf</cite></li>
			</ul>
		</div>
	</div>

	
	
</div>
<!-- forum_qpost -->

<div id="brd-stats" class="gen-content">
	<h2 class="hn"><span>Forum statistics</span></h2>
	<ul>
		<li class="st-users"><span>Total number of registered users: <strong>1</strong></span></li>
		<li class="st-users"><span>Newest registered user: <strong><a href="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3Byb2ZpbGUucGhwP2lkPTI%3D&amp;b=5">wolf</a></strong></span></li>

		<li class="st-activity"><span>Total number of topics: <strong>4</strong></span></li>
		<li class="st-activity"><span>Total number of posts: <strong>4</strong></span></li>
	</ul>
</div>
<div id="brd-online" class="gen-content">
	<h3 class="hn"><span>Currently online ( <strong>2</strong> guests, <strong>0</strong> registered users )</span></h3>

</div>

<div class="hr"><hr /></div>

<div id="brd-about" class="gen-content">
	<form id="qjump" method="post" accept-charset="utf-8" action="http://zend2.com/Def.php?u=Oi8vMTAuMC4wLjMvZm9ydW1zL3ZpZXdmb3J1bS5waHA%3D&b=5"><input type="hidden" name="convertGET" value="1">
	<div class="frm-fld frm-select">
		<label for="qjump-select"><span>Jump to forum:</span></label><br />
		<span class="frm-input"><select id="qjump-select" name="id">
			<optgroup label="Main Discussion">
				<option value="2">General</option>

				<option value="12">Antediluvian</option>
				<option value="22">Flood</option>
				<option value="26">Evolution</option>
				<option value="24">Astronomy</option>
				<option value="23">Geology</option>
				<option value="7">Civilisations</option>

				<option value="27">Philosophy</option>
				<option value="25">Library</option>
			</optgroup>
			<optgroup label="Forum Technical Support">
				<option value="6">Help</option>
				<option value="18">Suggestions</option>
			</optgroup>

		</select>
		<input type="submit" value="Go" onclick="return Forum.doQuickjumpRedirect(forum_quickjump_url, sef_friendly_url_array);" /></span>
	</div>
</form>
<script type="text/javascript">
		var forum_quickjump_url = "http://10.0.0.3/forums/viewforum.php?id=$1";
		var sef_friendly_url_array = new Array(11);
	sef_friendly_url_array[2] = "general";
	sef_friendly_url_array[12] = "antediluvian";
	sef_friendly_url_array[22] = "flood";
	sef_friendly_url_array[26] = "evolution";
	sef_friendly_url_array[24] = "astronomy";
	sef_friendly_url_array[23] = "geology";
	sef_friendly_url_array[7] = "civilisations";
	sef_friendly_url_array[27] = "philosophy";
	sef_friendly_url_array[25] = "library";
	sef_friendly_url_array[6] = "help";
	sef_friendly_url_array[18] = "suggestions";
</script>
	<p id="copyright">Powered by <strong><a href="http://zend2.com/Def.php?u=Oi8vcHVuYmIuaW5mb3JtZXIuY29tLw%3D%3D&amp;b=5">PunBB</a></strong>, supported by <strong><a href="http://zend2.com/Def.php?u=Oi8vd3d3LmluZm9ybWVyLmNvbS8%3D&amp;b=5">Informer Technologies, Inc</a></strong>.</p>
<p style="clear: both; ">The pun_repository official extension is installed. Copyright &copy; 2003&ndash;2009 <a href="http://zend2.com/Def.php?u=Oi8vcHVuYmIuaW5mb3JtZXIuY29tLw%3D%3D&amp;b=5">PunBB</a>.</p>

</div>

<!-- forum_debug -->

</div>
</div>

</body>
</html>

```


The website is accessible from internal and external, but external does not show the same layout.

---

### Post by mikejonesey on 2011-07-14
something in the source must be different if it displays differently... having a look now...

but i cant think how or why php would pump out different code based on host source...

---

### Post by gypsumwolf on 2011-07-14
I am hosting the site from my home/username/www/main directory
The forum is located here: /home/username/www/main/forums

The Apache2 sites-available default is:

```

<VirtualHost *:80>
        ServerAdmin admin@unserv.net
        ServerName ancienteon.com
        ServerAlias www.ancienteon.com

        DocumentRoot /home/wolf/www/main/
        <Directory /home/wolf/www/main/forums/>
                Options FollowSymLinks
                AllowOverride none
        </Directory>

        ScriptAlias /cgi-bin/ /usr/lib/cgi-bin/
        <Directory "/usr/lib/cgi-bin">
                AllowOverride None
                Options +ExecCGI -MultiViews +SymLinksIfOwnerMatch
                Order allow,deny
                Allow from all
        </Directory>

        ErrorLog ${APACHE_LOG_DIR}/error.log

        # Possible values include: debug, info, notice, warn, error, crit,
        # alert, emerg.
        LogLevel warn

        CustomLog ${APACHE_LOG_DIR}/access.log combined

    Alias /doc/ "/usr/share/doc/"
    <Directory "/usr/share/doc/">
        Options Indexes MultiViews FollowSymLinks
        AllowOverride None
        Order deny,allow
        Deny from all
        Allow from 127.0.0.0/255.0.0.0 ::1/128
    </Directory>

</VirtualHost>


```

---

### Post by gypsumwolf on 2011-07-14
You can take a look at the site:

[AncientEon.com]("AncientEon.com")

Click on Eon Forums link.

I can take a screen shot.

---

### Post by ikick on 2011-07-14
From here,

It looks like you are still trying to use local ip address ([http://ancienteon.com/forums/index.php;](http://ancienteon.com/forums/index.php;) clicking on the links take me to a local address).

Have you tried changing this in the PunBB settings?

---

### Post by gypsumwolf on 2011-07-14
Here is screen shot from outside:
[URL="http://www.2shared.com/photo/FoU5tjQu/snapshot1.html"]
http://www.2shared.com/photo/FoU5tjQu/snapshot1.html[/URL]


Here is INSIDE screen shot:

[http://www.2shared.com/photo/1CiA2ts9/snapshot2.html]("http://www.2shared.com/photo/1CiA2ts9/snapshot2.html")

---

### Post by gypsumwolf on 2011-07-14
No, I haven't tried to change that.

---

### Post by ikick on 2011-07-14
Yep - change the settings so it replicates your domain (instead of 10.0.0.x).

That should help fix it up and point to the correct image and script folders etc.

---

### Post by mikejonesey on 2011-07-14
two are same par

<script type="text/javascript">ginf={url:'http://zend2.com',script:'Def.php',target:{h:'http://ancienteon.com',p:'/forums/',b:''},enc:{u:'',e:'1',p:''},b:'5'}</script>
<script type="text/javascript" src="http://zend2.com/includes/main.js"></script>

and a div or two;

... must be somthing in punbb config...

strange... can you test this from another machine on your lan network... does it display right from there?

update: lol miles behind, watching tv at same time lol, keep up with the program... looks like u guys solved this...

---

### Post by ikick on 2011-07-14
> **mikejonesey said:**
> two are same par

<script type="text/javascript">ginf={url:'http://zend2.com',script:'Def.php',target:{h:'http://ancienteon.com',p:'/forums/',b:''},enc:{u:'',e:'1',p:''},b:'5'}</script>
<script type="text/javascript" src="http://zend2.com/includes/main.js"></script>

and a div or two;

... must be somthing in punbb config...

strange... can you test this from another machine on your lan network... does it display right from there?


It's the URL configuration. It would be incorrect for both of those sites, however if you take a look at a sample from the external source code:

```
<link rel="alternate" type="application/rss+xml" href="http://10.0.0.3/forums/extern.php?action=feed&amp;type=rss" title="RSS" />
<link rel="alternate" type="application/atom+xml" href="http://10.0.0.3/forums/extern.php?action=feed&amp;type=atom" title="ATOM" />
<link rel="top" href="http://10.0.0.3/forums" title="Forum index" />
<link rel="search" href="http://10.0.0.3/forums/search.php" title="Search" />
<link rel="author" href="http://10.0.0.3/forums/userlist.php" title="User list" />
<link rel="stylesheet" type="text/css" media="screen" href="http://10.0.0.3/forums/style/Oxygen/Oxygen.css" />
<link rel="stylesheet" type="text/css" media="screen" href="http://10.0.0.3/forums/style/Oxygen/Oxygen_cs.css" />
<!--[if lte IE 6]><link rel="stylesheet" type="text/css" href="http://10.0.0.3/forums/style/Oxygen/Oxygen_ie6.css" /><![endif]-->
<!--[if IE 7]><link rel="stylesheet" type="text/css" href="http://10.0.0.3/forums/style/Oxygen/Oxygen_ie7.css" /><![endif]-->

<!--[if IE 8]><link rel="stylesheet" type="text/css" href="http://10.0.0.3/forums/style/Oxygen/Oxygen_ie8.css" /><![endif]-->
<script type="text/javascript" src="http://10.0.0.3/forums/include/js/common.js"></script>

```

All the image, css, js etc point to the internal IP address, hence it only displays internally. Change it to a domain of your choice, and you should be on the way.

---

### Post by gypsumwolf on 2011-07-14
Thanks. That seems like the best solution. I am now woundering if I have to change all the source code in all the php files? or if there is a automatic way to do this in a config.

---

### Post by ikick on 2011-07-14
No worries at all. In the admincp of PunBB (assuming there is one), there should be the URL area. Generally this is in server settings or something similar, and all you'd need to do is change it from 10.0.0.3 to the domain of your choice.

Alternatively, you could go into the SQL database and try do this manually. 

Just saying - I've never really used PunBB however they are all generally the same. Let me know how that works and if you're able to find it.

---

### Post by gypsumwolf on 2011-07-14
Did a bit of searching and found it in config.php. I changed it.

nano config.php: (some things blanked for security)
```

  GNU nano 2.2.6                    File: config.php                                                

<?php

$db_type = 'BLANK_';
$db_host = 'localhost';
$db_name = 'BLANK_';
$db_username = 'BLANK_';
$db_password = 'BLANK_';
$db_prefix = '';
$p_connect = false;

$base_url = 'http://ancienteon.com/forums';

$cookie_name = 'forum_cookie_a753b5';
$cookie_domain = '';
$cookie_path = '/';
$cookie_secure = BLANK_;

define('FORUM', 1);

```

---

### Post by ikick on 2011-07-14
Awesome - I can see it's all working.

Hope that helped.

---

### Post by gypsumwolf on 2011-07-14
Thanks, it definitely did!.

The site may not 100% of the time work tonight since I am messing around with settings and other things. But, it should be up most the time after tonight.

---

