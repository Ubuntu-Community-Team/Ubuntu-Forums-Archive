---
title: "Help me Embed Video (html|css) webpage"
date: 2010-07-08
forum: General Help
---

### Post by luceerose on 2010-07-08
I am trying to embed a video in a webpage. I've had to experiment so much that I've ended up encoding the video to 3 different formats .ogv .mp4 .flv
& I've created a special video.html file just to test with. I've been trying for hours.

I've got the code written 2 different ways, both show up perfectly when accessed locally (screenshot 1).
But when I upload to my webspace & access the site from there, the videos don't show up properly (screenshot 2).

Also, although the videos don't show up when accessed from the web server, all 3 different files are accessible through firefox's Video DownloadHelper Add-On.

Here's my code for both attempts, if it helps;
```
<video controls>
<source src="videos/vanillapod.ogv" type="video/ogg; codecs=theora">
<source src="videos/vanillapod.mp4">
<source src="videos/vanillapod.flv">
<object data="flvplayer.swf" type="application/x-shockwave-flash">
<param value="flvplayer.swf" name="movie"/>
</object>
</video>
```
```
<video controls>
<source src="videos/vanillapod.ogv" type="video/ogg; codecs=theora">
<source src="videos/vanillapod.mp4">
<source src="videos/vanillapod.flv">
</video>
```
Here's how you can help;
Go to 
users.on.net/~larsenguitars/
and click on the TV Screen Icon in the upper left of my page & tell me if you can (see|right-click|download) the two videos there.

---

### Post by luceerose on 2010-07-09
Anyone ?

---

### Post by renkinjutsu on 2010-07-09
I went to your video.html and both videos work. This is tested on Google Chrome

---

### Post by luceerose on 2010-07-12
Ok, yes videos work on Chromium.
I have also got them to work on Firefox with the 'System Video' plugin
which puts html5 video through the browsers quicktime/gecko plugins,

But I cannot establish IE behaviour. I don't have access to a windows computer & don't have wine or anything.
Can someone test my site with IE please ???
As far as I know IE will require the Google Chrome Frame plugin;
```
http://ajax.googleapis.com/ajax/libs/chrome-frame/1/CFInstall.min.js
```
Can someone install the plugin in IE & verify this for me ?

---

