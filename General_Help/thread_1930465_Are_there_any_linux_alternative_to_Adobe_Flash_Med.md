---
title: "Are there any linux alternative to Adobe Flash Media Encoder??"
date: 2012-02-23
forum: General Help
---

### Post by colobix on 2012-02-23
Are there any linux alternatives to Adobe flash media server?
Free or not, doesn't matter.
As long as I can stream live video over flash (rtmp).

---

### Post by dragonfly41 on 2012-02-23
[LIST]
[*]Install tomcat 7 on Ubuntu
[/LIST]


[LIST]
[*]Deploy Red5 *.war in tomcat 7 webapps folder
[/LIST]

[INDENT][http://wiki.red5.org/wiki/1_0_RC1](http://wiki.red5.org/wiki/1_0_RC1)
[/INDENT]

---

### Post by colobix on 2012-02-23
Hmm. thanks, but this doesn't seem to be what I'm looking for.

---

### Post by evilsoup on 2012-02-23
I suggest you give [VLC](http://www.videolan.org/vlc/streaming.html) a look. I don't have any personal experience with streaming video, so I can't advise how to set anything up, but they have a [wiki](http://wiki.videolan.org/) and a [support forum](http://forum.videolan.org/) of their own.

It's in the repositories (and many people, including me, swear by it as a media player as well).

---

### Post by colobix on 2012-02-24
> **evilsoup said:**
> I suggest you give [VLC](http://www.videolan.org/vlc/streaming.html) a look. I don't have any personal experience with streaming video, so I can't advise how to set anything up, but they have a [wiki](http://wiki.videolan.org/) and a [support forum](http://forum.videolan.org/) of their own.

It's in the repositories (and many people, including me, swear by it as a media player as well).

VLC can't stream media. You can watch media and restream mms/rtsp streams. But you can't use vlc as a flash media server to stream from your capture card or webcam or anything of that nature.

---

### Post by dragonfly41 on 2012-02-24
If you're looking for **streaming video **I don't understand why you think Red5 doesn't meet that requirement.

[http://www.red5.org/](http://www.red5.org/)

---

### Post by dragonfly41 on 2012-02-24
Then why write this ..

> As long as I can stream live video over flash (rtmp).

---

### Post by lukeiamyourfather on 2012-02-24
> **renaxfbv said:**
> thanks, but this doesn't seem to be what I'm looking for

Really? it was designed as an alternative to Adobe Flash Media Server. That's like saying LibreOffice isn't an alternative to Microsoft Office.

---

### Post by colobix on 2012-02-24
> **lukeiamyourfather said:**
> Really? it was designed as an alternative to Adobe Flash Media Server. That's like saying LibreOffice isn't an alternative to Microsoft Office.
You mean tomcat?
I couldn't find version 7. I checked synaptic, and found version 6.
Didn't really understand it.
I installed it, but couldn't find it in the start menu, and I can't figure out how to start the program.
Are there any other alternatives?

---

### Post by dragonfly41 on 2012-02-24
Red5 will run o.k. on tomcat 6 

as to guidelines on running tomcat read here  [https://help.ubuntu.com/11.04/serverguide/C/tomcat.html](https://help.ubuntu.com/11.04/serverguide/C/tomcat.html)

check your Java setup.

But there might be easier options if you haven't dived into tomcat before this.

[EDIT]  You could try the Red5 server which is bundled with its own server.

[http://www.linkingpeopletogether.com/avblog/?p=8](http://www.linkingpeopletogether.com/avblog/?p=8)

---

### Post by lukeiamyourfather on 2012-02-24
> **colobix said:**
> You mean tomcat?
I couldn't find version 7. I checked synaptic, and found version 6.
Didn't really understand it.
I installed it, but couldn't find it in the start menu, and I can't figure out how to start the program.
Are there any other alternatives?

I was referring to Red5, I'm not familiar with Tomcat.

[http://trac.red5.org/wiki/Documentation](http://trac.red5.org/wiki/Documentation)
[http://tumbledesign.com/how-to-install-red5-0-9-on-ubuntu-10-04-lts/](http://tumbledesign.com/how-to-install-red5-0-9-on-ubuntu-10-04-lts/)

---

### Post by colobix on 2012-02-28
Thanks. I've had no luck with neither of them.
Found something called flvserver, no luck there either.
I'm a gui person. If something doesn't show up in the start menu, I'm not gonna use it. Basically because I have no idea how.
And I'm really not a terminal guy.

---

