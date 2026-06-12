---
title: "Selectively start X with two different xorg.conf's"
date: 2006-05-08
forum: General Help
---

### Post by PuleX on 2006-05-08
As noted in this other thread [1], X crashes for me when I start a video file if the xv-overlay is enabled and my tv is not connected (while the tv is defined in xorg.conf). This is somewhat troublesome. 

However, I read on the 'Sony Vaio and Ubuntu Linux howto' [2] that Vaio  be setup tocan select one of two different xorg.conf files (probably during startup?) depending on the graphics configuration selected. The howto explains it like this: 

> To use the Stamina/Speed switch, John Lathouwers (email) has written a little script to switch from one xorg.conf to another depending on the video chipset used. He uses two xorg.conf files in /etc/X11: xorg.conf.stamina and xorg.conf.speed. You then have to create a small script in /etc/init.d (called xorg_conf) with the following content:
```
VIDEO=`/usr/bin/lspci |grep -c nVidia`

if [ "$VIDEO" = 1 ]; then
cp -f /etc/X11/xorg.conf.speed /etc/X11/xorg.conf
else
cp -f /etc/X11/xorg.conf.stamina /etc/X11/xorg.conf
fi
```

Soft linking the script into rc2.d as S12xorg_conf will copy the correct xorg.conf file into place before X starts. 

Now I was wondering if it is possible to modify the script so it can pick up if a secondary monitor has been detected, and based on that loads one of two xorg.conf files. Anyone? Thanks in advance. 

[1] [http://ubuntuforums.org/showthread.php?t=86016](http://ubuntuforums.org/showthread.php?t=86016) 
[2] [http://ariel.vardi.free.fr/ariel/vaiosz.html](http://ariel.vardi.free.fr/ariel/vaiosz.html)

---

### Post by Zugzwang on 2008-01-16
Maybe this is of help:

[http://ubuntuforums.org/showthread.php?p=4146250]("http://ubuntuforums.org/showthread.php?p=4146250")

---

