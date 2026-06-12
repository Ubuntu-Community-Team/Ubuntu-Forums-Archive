---
title: "kernel: [ ] [drm] TV-14: set mode NTSC 480i 0"
date: 2010-10-05
forum: General Help
---

### Post by desconocido on 2010-10-05
I am getting this message in my syslog increasingly frequently.
> kernel: [ ] [drm] TV-14: set mode NTSC 480i 0

Anyone know what it means, who is writing it and how I can stop it?


It may be related to this bug:
[http://ubuntuforums.org/showthread.php?t=1387438](http://ubuntuforums.org/showthread.php?t=1387438)

I have begun to get the occasional sudden logoffs by Ubuntu.
Also, SketchUp under Wine has begun to malfunction - any mouse drag crashes the program, which is real downer right now.

About a month ago, I briefly connected an external monitor to my laptop. All these problems date from since then.

---

### Post by desconocido on 2010-10-06
Removing my /etc/X11/xorg.conf file seemed to cure the Wine/SketchUp problem. What's more, it's working with System->Preferences->Appearance->Visual Effects set to Normal (Before, I needed DRI off and Visual Effects set to None).

Weird, as I have deliberately not been downloading any Ubuntu updates.

Ubuntu version Karmic Koala 9.10
kernel version 2.6.31-22-generic

$X -version

X.Org X Server 1.6.4
Release Date: 2009-9-27
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.24-27-server i686 Ubuntu
Current Operating System: Linux faustino 2.6.31-22-generic #60-Ubuntu SMP Thu May 27 00:22:23 UTC 2010 i686
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-2.6.31-22-generic root=UUID=314dbdae-737c-49c2-b634-fc39d4564125 ro quiet splash
Build Date: 06 May 2010  09:30:46PM
xorg-server 2:1.6.4-2ubuntu4.3 (buildd@)

---

