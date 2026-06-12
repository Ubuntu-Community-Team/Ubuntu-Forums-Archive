---
title: "Unable to detect built in camera on my lap top"
date: 2010-03-14
forum: General Help
---

### Post by machosos on 2010-03-14
I have had this issue for a while now but never really messed with it enough to try and fix it...any ideas where to begin???

---

### Post by rnerwein on 2010-03-14
hi
run "lsusb" in a terminal and see if your webcam is prestent. for dokumentation have a look at:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)
[https://wiki.ubuntu.com/SkypeWebCams](https://wiki.ubuntu.com/SkypeWebCams)
i hope this will help you
ciao

---

### Post by machosos on 2010-03-14
yes it does see the camera there: 

machososjon@machososjon-laptop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
[B]Bus 001 Device 002: ID 0402:5603 ALi Corp. USB 2.0 Q-tec Webcam 300
[/B]Bus 001 Device 003: ID 0aec:3260 Neodio Technologies Corp. 7-in-1 Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:c521 Logitech, Inc. MX620 Laser Cordless Mouse
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

tried going thru the documentation a lil but not sure what i should try next...i cant unplug the camera or anything to test on another machine  because it is built in....any other ideas?

---

### Post by railen5 on 2010-03-14
Hello I am new to the forum, greetings to everyone,  

I had the same problem with my HP laptop. What I discovered was odd, I ended up doing a complete new install of Ubuntu from the disk because nothing I did would fix it, after reinstalling my webcam appeared using Cheese. 

I then retraced all my original steps i was following when my web cam first disappeared. After each change I made such as downloading new apps or software i would reload cheese to be sure the cam was still there. 

After loading libdvd4 and libdvdcss2 library so I can play encrypted dvd's a message comes up on the terminal saying a certain software is no longer needed and use the autoremove command to remove, i followed that advice, removed the software it mentions, opened up cheese and my webcam was gone. 

I then reinstalled the removed software using the command line and opened cheese and there was my webcam working fine, have had no problems ever since. I am sorry i do not remember which software was removed then reinstalled.

---

