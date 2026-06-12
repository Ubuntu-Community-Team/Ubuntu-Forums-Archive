---
title: "xmms-mp4 crashes"
date: 2006-01-24
forum: General Help
---

### Post by vegardh on 2006-01-24
Hi, I'm using the libs in xmms-mp4 to play the Ipod mini from gtkpod. The problem, it will typically crash when switching songs. Happens both when I'm using xmms and beep. (I just copied libmp4.* from /usr/lib/xmms/Input into /usr/lib/bme/Input to get mp4 in beep.) It will also happen when I, in xmms, play a directory of mp4 files, so I think it's a plain problem with the mp4 plugin. 

Typical crash message:
Segmentation fault
You've probably found a bug in XMMS, please visit
[http://bugs.xmms.org](http://bugs.xmms.org) and fill out a bug report.
Xlib: unexpected async reply (sequence 0x6b3a)!

My setup:
Breezy, universe and multiverse
marillat
freecontrib.org

It's a HP NC6000 laptop. 

Anyone got any clues? Any alternative packages for mp4 in xmms/beep worth trying?

---

### Post by endersshadow on 2006-01-24
Try this:

```
sudo apt-get install libmp4v2-0 libmp4v2-dev
```

You can also use Rhythmbox to play songs from your iPod, without going through gtkpod.  Also, gtkpod support for mp4 is a little spotty.  If you continue getting errors with gtkpod and mp4 files, try following the instructions under Transferring in this HowTo [here](http://ubuntuforums.org/showthread.php?t=114946).

---

### Post by vegardh on 2006-01-25
I already had libmp4v2-0, but that install job improved the situation still, for some reason, installing gcc in the same run... A bit strange that, but thanks.

---

### Post by endersshadow on 2006-01-25
[QUOTE=vegardh]I already had libmp4v2-0, but that install job improved the situation still, for some reason, installing gcc in the same run... A bit strange that, but thanks.[/QUOTE]

Perhaps you didn't have libmp4v2-dev?

At any rate, glad to hear it's working :-D

---

