---
title: "Sharing video over internet?"
date: 2011-05-05
forum: General Help
---

### Post by mrwooster on 2011-05-05
I have an old box running the latest ubuntu set up at home.  I use it to share files/media through my home network and also use it as an SSH gateway into my home network.

I would like to make the video files available for streaming over the internet using some sort of flash player or downloadable client.

What is the best way to do this?  I know you can stream using VLC, but I would like to be able to browser through my entire media directory remotely and select videos to play.  So I am either looking for server software that allows you to stream through flash, or some sort of client server setup where the client can display a list of remote media.

Thanks for any help

G

---

### Post by NoBugs! on 2011-05-05
You can install Apache to serve html pages and other files over your network, then put the movie file in the web directory, with an html page linking to it with a <video> tag:
[http://www.w3schools.com/html5/tag_video.asp](http://www.w3schools.com/html5/tag_video.asp)

---

### Post by dragonfly41 on 2011-05-05
Tomcat6 + red5

Synaptic Package Manager

install red5-server

---

