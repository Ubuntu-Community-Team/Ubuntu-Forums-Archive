---
title: "Pidgin 2.6.1"
date: 2009-08-22
forum: General Help
---

### Post by cygnis1 on 2009-08-22
Has anyone used the video chat in pidgin?

---

### Post by ram2008 on 2009-08-26
**I can't even find the video in 2.61, much less use it!  Don't know where they've hidden it.  I've gone through the program several times and can't find anything related to video.**

---

### Post by keastes on 2009-08-26
it is in the chat window under conversation>media>audio/video call.

no I've not tried it yet, no webcam gonna try audio tomorrow getting headset

---

### Post by ram2008 on 2009-08-26
OK, thanks for the info.  However, I notice that audio and video chats are grayed out.  Do I need to be in an actual chat to see/use those?  What about adjustments to the web cam?

---

### Post by edajai on 2009-08-26
i installed pidgin 2.6 but cant find the media option under conversation. Also in Help>About its shown :
Voice and Video: Disabled

How do i enable it?

---

### Post by 3rdalbum on 2009-08-26
Pidgin can only do voice and video in XMPP (Jabber) chats, and this support must be requested at compile-time. If you compiled Pidgin from source and you get "voice and video: disabled" in the About box, then you should recompile it again, but this time use:

```
./configure --help
```

to find out the actual options that the configure script has.

If you used a pre-built Debian package and voice and video is disabled, then contact the package maintainer or try building from source.

---

### Post by cygnis1 on 2009-08-26
So what you are saying is that if you can't configure pidgin or compile it, you are screwed.  Why is it that they tout the video messaging, then disable it by default?

---

### Post by keastes on 2009-08-29
its enabled in my 11 year old PC that i installed from the package, maybe it your sound input is not recognized/supported?

---

### Post by kevdog on 2009-08-29
I've used the audio portion, but not the video portion since I don't have a camera.  It worked after I removed pulse audio.  Additionally I did compile from source on Intrepid.  I believe for Jaunty there is a PPA repository version that is much easier to install.

---

### Post by cygnis1 on 2009-08-29
I don't know if my sound/video cards are supported as those oppitions are disabled.  I downloaded the get deb package and don't know how to enable the video/sound.

---

### Post by edajai on 2009-08-29
the debs from getdeb dont hav video n audio. use the ubuntu pidgin developers ppa instead.

---

