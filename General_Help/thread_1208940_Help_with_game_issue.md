---
title: "Help with game issue"
date: 2009-07-09
forum: General Help
---

### Post by Buck Buck on 2009-07-09
Hi All

I'm trying to get a fantastic game called Dominions 3 running. I just installed Ubuntu because I'm willing to give up Windows games like Medieval 2 Total War as long as I can have my Dominions 3 :)

Dominions 3 is linux friendly and I have the latest patch installed.

The issue I have is described by one other source on the www:

[http://forums.gentoo.org/viewtopic-t-559068-start-175.html?sid=194ac84976b73e25894b733284a28e7d](http://forums.gentoo.org/viewtopic-t-559068-start-175.html?sid=194ac84976b73e25894b733284a28e7d)

Specifically: 

"Hi, 
 
I have two machines, both AMD 64, !GB RAM. 
One has an ATI Radeon. 
One has a Matrox G450. 
 
Both ~amd64 newest kernel and xorg-server (1.4.0.90-r3), XFCE4.4 
When there is activity in a terminal (like emerging something), the X process uses a lot of CPU. 
 
Now, the ATI box is stable, no problems. 
**The Matrox box, however, locks regularly when playing dominions 3. Also, the mouse cursor gets corrupted. The mouse can be moved, but the system does not respond otherwise. **
I think it happens with xscreensaver from time to time, but this isn't really reproducible. 
 
OpenGL is probably the culprit. 
 
When, after the freeze, logging in via ssh, I see X at 100% CPU. If I kill it, or try to reboot the machine, it freezes completely. 
SysReq keys stop working. 
Ctrl+Alt+Backspace results in a hard shutdown as if pulling the wire (that's an old issue). 
The only way is to press reset."

I have Dell Inspirion 6400 with 256Mb ATI graphics card.

I'm going to turn off the Lavalamp screensaver and see if it helps, but from the above does anyone have any insights?

Any help is appreciated. I'll do some research on what X programs are today myself to see what I can learn, I thought I'd post here now because its Friday morning, I have to leave now for my 8 hours of work and then I have the evening to unwind. You know how it is when you have limited free time and you REALLY want something on the computer to work ;)

---

### Post by Buck Buck on 2009-07-11
Update: The problem is fixed. 

The issue was I was using Ubunti 9.04 and my graphics card (ATI Radeon Mobility X1300) is incompatible with 9.04. 

I installed Ubuntu 8.04 and installed the ATI driver for my graphics card (note: the Add/Remove program had the ATI driver listed, but the www location it is directed to returns a 404 error ie the file is not there. I searched for the file in google and found it at [http://molinux.jccm.es/molinux/ubuntu_pool/pool/restricted/l/linux-restricted-modules-2.6.24/](http://molinux.jccm.es/molinux/ubuntu_pool/pool/restricted/l/linux-restricted-modules-2.6.24/) ). Now all works brilliantly!

:)

---

