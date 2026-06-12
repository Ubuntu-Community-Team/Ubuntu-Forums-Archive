---
title: "lirc with Jetway ION2 chipset"
date: 2011-01-27
forum: General Help
---

### Post by ssarkar on 2011-01-27
I just installed 10.10 on a Jetway HBJC600C99-52W machine.  It has the NVIDIA ION2 chipset.  Through a lot of struggles, I have managed to get most of the computer working well with Linux.  The part that I'm still struggling with is the remote control.  With Ubuntu out of the box, perhaps about 1/3 of the buttons are recognized.

From additional research, it looks like lirc is supposed to address this issue.  I tried installing lirc however, after installation the only thing that shows up is /dev/lircd.   I was expecting something like /dev/lirc0.

I've tried is via

sudo apt-get install lirc
and then I picked the Windows Media Center receiver

I also tried what was in this thread
[http://ubuntuforums.org/showthread.php?t=1645241](http://ubuntuforums.org/showthread.php?t=1645241)
however, that seems to be on a different jetway model, an NVIDIA ION chipset instead of an ION2 and the driver install for the IR receiver didn't work for me.  

I was wondering if anyone had success installing lirc and getting all the keys on their remote working.  Thanks.

---

### Post by Grezk on 2011-01-31
Hi, I bought one of these and have been setting it up over the last few days. I managed to get the remote functioning a bit closer to how it should by installing the hid-aureal drivers as per this setup guide over on the xbmc forums:

[http://forum.xbmc.org/showpost.php?p=699886&postcount=170](http://forum.xbmc.org/showpost.php?p=699886&postcount=170)

However this still doesn't get all the buttons working as you would expect. I got a bit closer by installing lirc and pointing it to the Linux input layer and choosing a /dev/input/eventX device (had to try a few). This gets most things working as expected.

Only thing I'm missing now is to try and remap some of the more useless buttons on the remote to functions it doesn't have, such as the context menu.

---

### Post by Grezk on 2011-02-01
Got this working and no need for lirc thanks to this thread on the xbmc forum - [http://forum.xbmc.org/showthread.php?p=710064#post710064](http://forum.xbmc.org/showthread.php?p=710064#post710064)

---

