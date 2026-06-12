---
title: "New update of flash/firefox won't load videos"
date: 2010-07-29
forum: General Help
---

### Post by camelface on 2010-07-29
So yesterday, either flash or firefox was updated, and now youtube videos cannot be loaded. It seems every second update has problems. Is there a way to fix this simply?

---

### Post by RabbitWho on 2010-07-29
I think youtube are fecking with things, because there's this stupid gray bar down the bottom every now and then, and suddenly I can't download videos. 
I hate those bars on facebook, on bebo, but that doesn't matter.. now they have them on omg ubuntu and youtube.. ARGH! Who thought of them!? I'd like to smack him! 

It might well be a youtube problem? Anyone else having trouble? I'm gonna see how things are tomorrow.

Are other video sites working? 
[http://vimeo.com/](http://vimeo.com/)

---

### Post by lovinglinux on 2010-07-29
Type **about[noparse]:[/noparse]config** in Firefox address bar, then type **plugin.expose_full_path** in the filter, then double-click the same item in the results to make it **true**. Then type **about[noparse]:[/noparse]plugins** in the address bar, find Shockwave Flash, copy the corresponding Path and Version and paste here.

---

### Post by camelface on 2010-07-29
File:  /usr/lib/flashplugin-installer/libflashplayer.so
Version:   Shockwave Flash 10.1 r53

the internet is acting weird

---

### Post by lovinglinux on 2010-07-29
> **camelface said:**
> File:  /usr/lib/flashplugin-installer/libflashplayer.so
Version:   Shockwave Flash 10.1 r53

the internet is acting weird

First try [FLASH-AID](http://flash-aid-extension.blogspot.com). Make sure you get version 1.0.10.

---

### Post by camelface on 2010-07-30
can't find the download button

---

### Post by lovinglinux on 2010-07-30
> **camelface said:**
> can't find the download button

Get it from Mozilla then: [https://addons.mozilla.org/en-US/firefox/addon/161939/](https://addons.mozilla.org/en-US/firefox/addon/161939/)

The latest version has been approved already and is available on the link above.

---

### Post by lavadisco on 2010-07-31
Flash and Firefox are definitely acting weird. I can play videos on Youtube, but not if they're embedded on another website. I also cannot fullscreen certain Youtube vids. I have Flashaid 1.0.10, but it didn't seem to help.

---

### Post by lovinglinux on 2010-07-31
> **lavadisco said:**
> Flash and Firefox are definitely acting weird. I can play videos on Youtube, but not if they're embedded on another website.

[http://ubuntuforums.org/showthread.php?t=1490688](http://ubuntuforums.org/showthread.php?t=1490688)

> **lavadisco said:**
> I also cannot fullscreen certain Youtube vids. I have Flashaid 1.0.10, but it didn't seem to help.

[http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html](http://firefox-tutorials.blogspot.com/2010/06/flash-issues-solutions.html)
[http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html](http://firefox-tutorials.blogspot.com/2010/05/flash-optimization.html)

---

### Post by lavadisco on 2010-07-31
> **lovinglinux said:**
> [http://ubuntuforums.org/showthread.php?t=1490688](http://ubuntuforums.org/showthread.php?t=1490688)

Thanks! In the end the problem was fixed by changing my visual effects setting from "normal" to "none". Bizarre.

---

