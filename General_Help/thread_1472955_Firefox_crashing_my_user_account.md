---
title: "Firefox crashing my user account"
date: 2010-05-04
forum: General Help
---

### Post by Donut417 on 2010-05-04
I have a weird Issue that just started today. Ill open up a new tab in Firefox and the screen goes black and takes me back to the log in screen. Im using Lucid Lynx. If it helps it mostly happens on flash based sites. I have flash block installed but it doesn't always help. Also it happens on random sites. But im not sure why this would log me out. And answers would be helpful.

---

### Post by lovinglinux on 2010-05-05
Try to uninstall libmoon package.

```
sudo apt-get remove libmoon
```

---

### Post by utnubuuser on 2010-05-05
try removing the search box by right-clicking firefox's panel, selecting Customize..., then grabbing the search-box and placing it in the pop-up dialog.

You can restore it the same way.

---

### Post by lovinglinux on 2010-05-05
> **utnubuuser said:**
> try removing the search box by right-clicking firefox's panel, selecting Customize..., then grabbing the search-box and placing it in the pop-up dialog.

You can restore it the same way.

??? 

I don't think this is what the OP is asking for.

---

### Post by Donut417 on 2010-05-05
> **lovinglinux said:**
> Try to uninstall libmoon package.

```
sudo apt-get remove libmoon
```

Got a not installed message. This is why I hate adobe. Them and there crapy programing skills.

---

### Post by tekstr1der on 2010-05-05
> Ill open up a new tab in Firefox and the screen goes black and takes me back to the log in screen...

Looks like you have the issue described in this bug:

Lucid 2.6.32-16 crashed to login screen - miCopyRegion
[https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772](https://bugs.launchpad.net/ubuntu/+source/xorg-server/+bug/539772)

Found this because my Firefox has started segfaulting after some random amount of time. Unfortunately my behavior is different in that X doesn't crash entirely, just Firefox CTD.

---

### Post by lovinglinux on 2010-05-05
Check if you have the proper flash version. See the [[COLOR="Sienna"]**Flash Optimization**[/COLOR]](http://lovinglinux.megabyet.net/?page_id=220#Flash--Optimization-1) section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

### Post by Donut417 on 2010-05-06
So far so good. Hopefuly it keeps working. :D

---

