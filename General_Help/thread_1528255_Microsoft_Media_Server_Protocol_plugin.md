---
title: "Microsoft Media Server Protocol plugin"
date: 2010-07-10
forum: General Help
---

### Post by jereece on 2010-07-10
I like to watch NASA TV - [http://www.nasa.gov/multimedia/nasatv/](http://www.nasa.gov/multimedia/nasatv/), however when I go there Ubuntu says I need the Microsoft Media Server Protocol plugin and it offers to search for it.  The search finds no acceptable plugin.  I have tried this in Firefox and Google Chrome.  Any suggestions?

Thanks,
Jim

---

### Post by Steve603z on 2010-07-10
you don't need to use the web browser to view the video on the website, you can open the video directly using a video player, video plugins for web browsers in ubuntu are a little buggy sometimes, this is one of those cases

Using Totem (the default ubuntu comes with) press Alt + F2 and type:
```
totem http://www.nasa.gov/55644main_NASATV_Windows.asx
```
Using VLC press Alt + F2 and type:
```
vlc http://www.nasa.gov/55644main_NASATV_Windows.asx
```

also, to make sure the proper codecs are installed, I recommend installing the "ubuntu restricted extras package" if you haven't already
```
sudo apt-get install ubuntu-restricted-extras
``` 
[http://en.wikipedia.org/wiki/Ubuntu-restricted-extras](http://en.wikipedia.org/wiki/Ubuntu-restricted-extras)

---

### Post by lovinglinux on 2010-07-11
I have no problems watching it. Just follow the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") to install necessary codecs and gecko-mediaplayer plugin.

---

### Post by Steve603z on 2010-07-11
> **lovinglinux said:**
> I have no problems watching it. Just follow the [Comprehensive Multimedia & Video Howto]("http://ubuntuforums.org/showthread.php?t=766683") to install necessary codecs and gecko-mediaplayer plugin.

for whatever reason, it'll try to connect for me then say "stopped" when using the mplayer-plugin

so I just copy the URL and open it in VLC instead

---

