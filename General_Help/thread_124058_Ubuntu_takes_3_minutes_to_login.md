---
title: "Ubuntu takes 3 minutes to login"
date: 2006-01-31
forum: General Help
---

### Post by Haegin on 2006-01-31
It is either since I reinstalled (recently on a new set of hard drives and a new mobo) or since I installed prelinking (which I have subsequently turned off to no avail) or possibly since I changed my splashscreen but my system has slowed down to a 3 minute login time on an Athalon XP 2500 whereas on my old system it all took seconds. What log files do I need to look through and where can I find them.
Also where can I reset my splash-screen stuff to see if that is the problem.

Thanks

EDIT: Just timed again and its up to 4.20 to a fully functioning desktop..

---

### Post by Sutekh on 2006-01-31
What part of the boot up takes 4:20?  The whole boot up process, or the part after logging in before you get a fully-functioning desktop?

If the latter, check this link [Ubuntu Forums - HOWTO Speed up the Ubuntu boot process - the way you can feel it]("http://ubuntuforums.org/showthread.php?t=89491")

As for the splash screen
[http://www.ubuntuforums.org/showpost.php?p=523168&postcount=6]("http://www.ubuntuforums.org/showpost.php?p=523168&postcount=6")

---

### Post by AmboyGuy on 2006-01-31
For Splash try changing /boot/grub/menu.lst
```
kernel        /boot/vmlinuz-2.6.12-10-686 root=/dev/hda1 ro quiet splash

``` to no-splash.
Have you used BUM or sysvrc-conf to not load modules you aren't using ? ie. bluetooth, laptop stuff when you're a desktop - like battery checking routines, cut out hplibs & cups if you don't have a printer etc.
Worked for me cut about a minute on my 450Mhz P3.
Also since it's a new mother board that you have the BIOS & any Jumpers configured properly for full speed CPU and services.

---

