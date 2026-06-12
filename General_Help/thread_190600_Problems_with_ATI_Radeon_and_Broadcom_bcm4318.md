---
title: "Problems with ATI Radeon and Broadcom bcm4318"
date: 2006-06-06
forum: General Help
---

### Post by mochaspro on 2006-06-06
Hey guys, first of all thank you for reading this.

I just bought a laptop: HP Pavilion dv800, amd Turion 64 bits, ATI Radeon Xpress 200M and a Broadcom BCM4318 [AirForce One 54g]

My problems are (and im sure im not alone with this) that i can't have 3D acceleration and i can't use my Wireless...

Now i'll tell you guys what i've doing for more than 2 weeks:

**_About 3D acceleration:_**

- I tried to install the fglrx drivers in the repositories
- I tried to install the ATI driver from the page (the 34.6 MB file) and i did it in 2 ways... creating the deb files and then installing them with dpkg and just running it and installing.
- I tried to download a file i saw somewhere (a rpm) fglrx_6_8.... and i used alien and then tried to install the .deb 

With all of that I modify the xorg.conf with a lots of things, adding some Options in the Device Section like:

- Option "VideoOverlay" "on"
- Option "OpenGLOverlay" "off"
- Option "UseInternalAGPGART" "no"

i added this modules too:

- modprobe agpgart
- modprobe -r fglrx 

and if you are thinking this: yes, i installed headers and restricted modules for my kernel

so as you can notice i'll be doing a lot of things without success... 

Sometimes i got this error too: when the X (gdm) is starting i can see the desktop BEFORE i can log in, then the login screen appears, after that i can see everything real slowly and if i write fglrxinfo i see like all it's good, nothing about mesa, but a few minutes after my computer freeze... if this is not happening i see the MESA stuff with fglrxinfo....

And yes, i changed the UMA thing in the bios, i have 256 ram in video, 128 by the card and 128 by the ram...

**_About the Wireless:_**

I tried 3 things:

- Using different kinds of win drivers with ndiswrapper: the winXP 64 bits, the WinXP 32 bits
- Using the bcm43xx-fwcutter
- Using a script that comes in the repositories (it download, extract and install a driver) but no success.

Now the led in the computer turns on and off if i do sudo ifconfig eth1 up/down and SOMETIMES i can sudo iwlist eth1 scan and see available ESSIDS, but never ever i can get an IP with dhclient or whatever :S

I hope you can help me with this guys because i love linux and i dont want to use Windows or that in my machine :)

Thank you

---

### Post by H.E. Pennypacker on 2006-06-06
Your problem with the BCM4318 card may very well be the same as that of other people, including myself.  I'd suggest using the search feature first, and use that to find a solution, because BCM4318 users have already received a lot of attention on this board, as well as other places.  

As for your other problem, first seperate the two issues you're having.  It's better to deal with only one issue in a thread for reasons of better organization, and others will find your thread more quickly.

---

### Post by bust_er on 2006-11-02
Mis-posted

---

### Post by bust_er on 2006-11-02
mis-posted

---

