---
title: "Stream from Webdav?"
date: 2011-01-09
forum: General Help
---

### Post by dboy1612 on 2011-01-09
Hi there,

I was wondering if anyone happened to know how to or if it is even possible to stream from a webdav connection? Now, yeah, that sounds a bit weird, but lemme explain.

I say stream to fit my example. Lets say I have a video saved on a webdav server, and have the webdav mounted in ubuntu with davfs2 (if anyone has something better lemme know!). Now, when I click to run this video in VLC for example, what happens is that the video has to be completely downloaded to the ubuntu system before it starts playing.

My question is, is it possible to have the video start playing AS it downloads? So lets say it's a 100mb video, and after 5mb is downloaded the video can begin playing. Now I don't need it to be specifiaclly 5mb before it starts playing or anything like that, it's just example. Though it would be nice too. XD

Any help is appreciated! Thanks! :D

---

### Post by tvjohn on 2012-01-10
> **dboy1612 said:**
> Hi there,

I was wondering if anyone happened to know how to or if it is even possible to stream from a webdav connection? Now, yeah, that sounds a bit weird, but lemme explain.

I say stream to fit my example. Lets say I have a video saved on a webdav server, and have the webdav mounted in ubuntu with davfs2 (if anyone has something better lemme know!). Now, when I click to run this video in VLC for example, what happens is that the video has to be completely downloaded to the ubuntu system before it starts playing.

My question is, is it possible to have the video start playing AS it downloads? So lets say it's a 100mb video, and after 5mb is downloaded the video can begin playing. Now I don't need it to be specifiaclly 5mb before it starts playing or anything like that, it's just example. Though it would be nice too. XD

Any help is appreciated! Thanks! :D

It is. I've been doing this whilst testing over the last few days. I'm afraid this isn't using Ubuntu or davfs2, but an embedded Linux on a small media player, & lighttpd with the mod_webdav library enabled.

I've also been doing exactly that with VLC! Again, not Ubuntu, but VLC on a mac. Using the same media player as server, I initially tested video just by double-clicking on the file in the desktop mounted webdav folder, & it downloaded it which took ages as you discovered!

So, up to VLC's File menu, select "Open network...", then enter the URL for the movie, for example:

[http://192.168.2.100/movie/AliceInWonderland.mov](http://192.168.2.100/movie/AliceInWonderland.mov)

in my LAN setup, & it started playing in a few seconds. 

All this I'm doing over wifi, but naturally ethernet is best for hi def' video.

WebDAV seems quite important now with so many iPad's etc. around, as many apps rely on webDAV to transfer data.

HTH.

---

