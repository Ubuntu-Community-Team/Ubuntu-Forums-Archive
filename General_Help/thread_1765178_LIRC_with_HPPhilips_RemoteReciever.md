---
title: "LIRC with HP/Philips Remote/Reciever"
date: 2011-05-22
forum: General Help
---

### Post by earthmeLon on 2011-05-22
A long time ago, HP used to give out a small 'ExpressCard' remote that would fit into your ExpressCard slot when you purchased a laptop. Also included was a USB IR receiver and remote.

I am interested in getting the USB IR receiver working.  Currently, I am able to use VOLUME UP and VOLUME DOWN, but it is very inconsistent (ie: I mash the button 20 times until audio volume drops).

The IR receiver has a model number of OVU422000/06 (although, I have another, larger version somewhere in my house)
```
 ~$ lsusb
Bus 010 Device 002: ID 0471:060c Philips (or NXP) Consumer Infrared Transceiver (HP)
```

The remote has these numbers:  RC1804911/06  and P/N:438584-001.  Here is a picture
[IMG]http://ittyb.it/images/a0b6fdb9.jpg[/IMG]



I am having a hard time figuring out what setup to use whenever I install LIRC.

Does anybody know which options to select to get this working, or if there is a 'generic' mode that I can use to manually map keys?  Is there another alternative to LIRC?

Thanks in advance :D

---

### Post by earthmeLon on 2011-05-22
Solution:

sudo apt-get install lirc OR sudo dpkg-reconfigure lirc

Select "Windows Media Center Transceivers/Remotes (all)"
Select "None"

Then run 'irw' and press buttons on the remote.  You should see text such as:
000000037ff07be1 00 Up mceusb
000000037ff07bdf 00 Left mceusb

---

