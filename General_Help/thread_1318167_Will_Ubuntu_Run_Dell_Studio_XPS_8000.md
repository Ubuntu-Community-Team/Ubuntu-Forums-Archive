---
title: "Will Ubuntu Run? Dell Studio XPS 8000"
date: 2009-11-07
forum: General Help
---

### Post by rinoshea on 2009-11-07
[FONT=Arial Narrow][SIZE=2]I'm planning to buy a new desktop. I'd like to run Ubuntu **64bit** on it. _Can anyone tell me any problems they see in this configuration. _
[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]
[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]**Processors**:
Studio XPS 8000, Intel® Core™ i7-860 processor (8MB Cache, 2.80GHz**)**[/SIZE][/FONT]
[FONT=Arial Narrow][SIZE=2]**Memory**:
6GB Dual Channel DDR3 SDRAM at 1066MHz - 4 DIMMs[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]
[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]**Hard Drives**:
750GB - 7200RPM, SATA 3.0Gb/s, 16MB Cache[/SIZE][/FONT][FONT=Arial Narrow]
[/FONT][FONT=Arial Narrow][SIZE=2]**Video Card**:
nVidia GeForce GTX260 1792MB[/SIZE][/FONT][FONT=Arial Narrow]
[/FONT][FONT=Arial Narrow][SIZE=2][IMG]http://i.dell.com/images/global/configurator/general/spacer.gif[/IMG][/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]**Sound**:
Soundblaster X-Fi MB – Software Enabled[/SIZE][/FONT][FONT=Arial Narrow][SIZE=2]
[/SIZE][/FONT]

---

### Post by rinoshea on 2009-11-07
BUMP

I really don't want to buy this without some assurance that Ubuntu x64 will run well.

---

### Post by UranUtan on 2009-11-07
Hi,

Ubuntu 9.10 x64 will run more than fine on this dream machine. 

It's an Intel Core i7 !!! I don't know if you know but it can even run Virtual Machine with Nested Paging feature enabled (a kind of hardware VT feature that will boost VM performance). In other words, it's a very high end machine. You are good to run all Ubuntu versions for at least the next 10 years.

---

### Post by lagamemnon on 2009-11-19
Hold your horses if it's not too late!

I just got this machine, installed Ubuntu 9.10 64 bit and the network card does not work AND I can't seem to find the drivers for it. 

As of now, I still haven't figured out how to get internet working on it.

This was my post about that problem that was ignored:
[http://ubuntuforums.org/showthread.php?t=1298210](http://ubuntuforums.org/showthread.php?t=1298210)

---

### Post by ndz on 2009-11-22
Please keep us posted if you get that network card working.  I am considering the same system the OP mentioned.

---

### Post by mortski on 2009-12-03
I've installed Karmic on a XPS 8000 and had no issues with the wired networking. The wireless worked after I installed the Broadcom STA wireless driver from the Hardware Drivers app under System->Administration.

---

### Post by kodrbee on 2009-12-11
yes, in a breeze. wireless works fine for me too. but as said in the previous post, you need to install the Broadcom STA wireless driver from the Hardware Drivers app under System->Administration
note that the driver's list is empty in case you're not yet connected to the internet. but you can install the drivers from the Ubuntu install CD. go to Software Sources under System->Administration and make sure that the option to install packages from the CD is checked. then insert the CD and re-open the Hardware Drivers dialog. now you should be able to install the proprietary Broadcom STA wireless driver.
conclude with configuring your wireless connection in the Network Connections dialog under System->Preferences

---

### Post by ndz on 2010-01-23
Any other updates?  How is this system working out for you all with Karmic 64-bit?

I just (finally) ordered the same system.

---

### Post by rinoshea on 2010-03-24
Sorry for getting back so incredibly late. I actually decided on the XPS 9000 instead of the 8000, and everything is working perfectly. 

Sorry I can't help with the networking.

---

