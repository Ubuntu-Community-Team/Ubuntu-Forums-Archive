---
title: "Wacom Intuos5 in Ubuntu 12.04"
date: 2012-06-26
forum: General Help
---

### Post by cazazo on 2012-06-26
Hi all, does any one know how to make Intuos5 work under ubuntu 32bit 12.04? I have installed the libraries from  linuxwacom project but still nothing.
thanks

---

### Post by Favux on 2012-06-26
Hi cazazo,

> I have installed the libraries from linuxwacom project but still nothing.
Did you install the wacom.ko from input-wacom-0.13.0 and update your xf86-input-wacom?

Instructions for doing both are on either of these HOW TOs.
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

---

### Post by cazazo on 2012-06-26
The tablet is now working! Now it's just a mater of learn how to tweak it! Thank you Favux! Great stuff!

---

### Post by Favux on 2012-06-26
Great!  :)

As far as tweaking goes you might want to take a look at:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Tablet_Configuration)  on:  [http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO](http://sourceforge.net/apps/mediawiki/linuxwacom/index.php?title=Category:HOWTO)

---

### Post by cazazo on 2012-06-26
Once again, thank you very much!!! 
Will play with the config tonight!

---

### Post by cazazo on 2012-06-26
Favux, there is by any chance the possibility to configure the multi touch features? For zoom, rotation etc?

---

### Post by Favux on 2012-06-26
You can use the xsetwacom settings to change zoom.  But there isn't a rotation or pivot.  That got left out somewhere, cause I'm pretty sure we had it briefly on the forum when we were developing the original BambooPT touch gestures.

Unfortunately Peter Hutterer grandfathered gestures and doesn't want new ones added to the driver.  Just bug fixes etc.

You can call the manuals in a terminal:
man wacom
man xsetwacom

But you could place touch on the evdev or Synaptics driver for example.  And with evdev you could use ginn.

Something else you might want to look at is EasyStroke.

---

### Post by catrincm on 2012-08-05
> **Favux said:**
> Hi cazazo,


Did you install the wacom.ko from input-wacom-0.13.0 and update your xf86-input-wacom?

Instructions for doing both are on either of these HOW TOs.
[http://ubuntuforums.org/showthread.php?t=1515562](http://ubuntuforums.org/showthread.php?t=1515562)
[http://ubuntuforums.org/showthread.php?t=1038949](http://ubuntuforums.org/showthread.php?t=1038949)

My "Wacom Driver Settings" (under System Settings) had said no tablet found; just installing wacom.ko worked for me, with instructions from the first link from Favux, and search for "[SIZE=2]Install input-wacom-0.13.0's wacom.ko[/SIZE]". This then worked after restarting without having to update the xf86-input-wacom; however I needed to change to left-handed orientation to get the normal work even though I am using it right handed.

---

### Post by Favux on 2012-08-05
Hi catrincm,

What release of Ubuntu are you using?  For example Precise 12.04.

---

