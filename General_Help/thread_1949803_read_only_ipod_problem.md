---
title: "read only ipod problem"
date: 2012-03-30
forum: General Help
---

### Post by sreplow on 2012-03-30
Hi folks, relative noob here looking for help:

I just got a new iPod Nano (the tiny ones with the touchscreens).  

I first plugged it into my Mac and named it, and now when I plug it into 10.04.4 and try and add songs in Rhythmbox it says that the device has read-only permissions and wont allow it, though I can transfer songs from the iPod to the computer.  

I flipped through a few posts to see if there was a cut and dry answer for this but I couldn't find anything.  I did install  gtkpod (sudo apt-get install gtkpod) and that did not change anything.  

lsusb: Bus 002 Device 005: ID 05ac:1266 Apple, Inc. 
ls -l /media: drwxr-xr-x 1 root root   13 2012-03-30 22:04 pw__nano


Anybody have any ideas on what the real problem is, or what to do to fix it?  

I know I can use my Windows VM if I have to, or use Wine to install iTunes but I'm saving that as my last resort. 


Thanks for the help-

---

### Post by raja.genupula on 2012-03-30
have a look at this
[https://help.ubuntu.com/community/Mount/USB#Device_become_suddenly_read_only](https://help.ubuntu.com/community/Mount/USB#Device_become_suddenly_read_only)

---

