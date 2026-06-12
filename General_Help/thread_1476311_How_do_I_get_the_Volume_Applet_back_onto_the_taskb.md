---
title: "How do I get the Volume Applet back onto the taskbar 10.04?"
date: 2010-05-07
forum: General Help
---

### Post by ozguitarplayer on 2010-05-07
Hi,
10.04
I managed to delete the Volume Applet that appears by default on the task bar. I'm sure it used to be listed in 'Add to Panel' in other version of Ubuntu however I can't see it there in 10.04.
Can someone explain to me how I get it back?

---

### Post by coolcaseley67 on 2010-05-07
hi 

-its in Add to Panel choose notification area or long the lines of that .

hope it helps !!! :guitar:

---

### Post by bryanl on 2010-05-07
see [http://ubuntuforums.org/showthread.php?t=1469771&page=2](http://ubuntuforums.org/showthread.php?t=1469771&page=2)

> go to System > Preferences > Startup Applications

in the startup tab, look for 'Volume Control' and check it if its unchecked.

If its not there, 'Add' it using the following parameters:

Name: Volume Control
Command: gnome-volume-control-applet
Comment: Show desktop volume control

...and then restart....

As noted, it got integrated into the notify panel and if you remove that you loose the volume control. This applet is what the previous version used for volume as its own thing in the panel.

---

### Post by ozguitarplayer on 2010-05-08
thanks for that..all's good

---

### Post by kleinebre on 2010-09-14
> **bryanl said:**
> see [http://ubuntuforums.org/showthread.php?t=1469771&page=2](http://ubuntuforums.org/showthread.php?t=1469771&page=2)



As noted, it got integrated into the notify panel and if you remove that you loose the volume control. This applet is what the previous version used for volume as its own thing in the panel.

If you want a standalone volume control applet, use gnome-volume-control-applet. If that doesn't work or if it keeps waiting for the sound system to become active (did you uninstall pulseaudio??) search for volti instead.

---

