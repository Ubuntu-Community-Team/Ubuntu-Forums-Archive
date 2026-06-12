---
title: "Webcam stopped working in 9.10 (worked in 810)"
date: 2010-03-09
forum: General Help
---

### Post by dgrafix on 2010-03-09
Logitech webcam:
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 023: ID 056a:0062 Wacom Co., Ltd 
Bus 001 Device 013: ID 045e:00d2 Microsoft Corp. 
Bus 001 Device 010: ID 1241:1503 Belkin Keyboard
Bus 001 Device 008: ID 046d:09a1 Logitech, Inc. QuickCam Communicate MP/S5500
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB

It has a mic built in and heard there was a blacklist hack soemwhere to get it fixed.
Anyone know?

---

### Post by no2498 on 2010-03-09
this is for the webcam
open a terminal type ( gstreamer-properties ) click enter
click video try v4l1 and v4l2 click the bottom test button for each 1

if gstreamer is not installed
go to add/remove type gstreamer and install it

try the cam in ekiga softphone its loaded already

a lot of programs see my cam now

i would say try cheese but i have had to do this 15 times to keep my cam working

i like wxcam [http://wxcam.sourceforge.net/](http://wxcam.sourceforge.net/)

getdeb also has it

---

### Post by dgrafix on 2010-03-10
[http://ubuntuforums.org/showpost.php?p=7205851&postcount=4](http://ubuntuforums.org/showpost.php?p=7205851&postcount=4)

this might do it :/


Edit yes it worked!

PS, thanks for the gstreamer-properties tip, a handy way of trying it :)

---

### Post by no2498 on 2010-03-10
your welcome look in the cheese help files faq's

unplug the cam first if your computer starts to run hot like the fan runs fast
it tells you to set the plugin to     .x Window system (no xv)

---

### Post by no2498 on 2010-03-10
ok for the sound with the mic 
right click the speaker icon up top click preferences
and start playing

---

### Post by railen5 on 2010-03-15
Hello I am new to the forum, greetings to everyone,  

I had the same problem with my HP laptop. What I discovered was odd, I ended up doing a complete new install of Ubuntu from the disk because nothing I did would fix it, after reinstalling my webcam appeared using Cheese. 

I then retraced all my original steps i was following when my web cam first disappeared. After each change I made such as downloading new apps or software i would reload cheese to be sure the cam was still there. 

After loading libdvd4 and libdvdcss2 library so I can play encrypted dvd's a message comes up on the terminal saying a certain software is no longer needed and use the autoremove command to remove, i followed that advice, removed the software it mentions, opened up cheese and my webcam was gone. 

I then reinstalled the removed software using the command line and opened cheese and there was my webcam working fine, have had no problems ever since. I am sorry i do not remember which software was removed then reinstalled.

---

