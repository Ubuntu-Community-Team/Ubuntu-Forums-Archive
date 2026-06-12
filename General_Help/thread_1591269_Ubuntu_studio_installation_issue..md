---
title: "Ubuntu studio installation issue."
date: 2010-10-09
forum: General Help
---

### Post by amit.kanade1983 on 2010-10-09
Hi forum,
         I downloaded and tried to install ubuntustudio-10.04-alternate-i386 on my pc.I burned the image on a dvd and booted my pc from the dvd.the problem is, the setup is detected but when i get the language selection page the OS gets stuck,even if i try to choose options it doesnt let me do it...its like the system hangs and nothing happens even if i press any key on the keyboard...can smone tell me why this happens and what is the solution for this. 
I am new to linux.

---

### Post by amit.kanade1983 on 2010-10-09
also my system configuration is as follows.

Intel(R) core(TM) 2 duo cpu E4600 @ 2.4Ghz.
2 GB Ram.
250 gb SATA HD.
No special graphics and sound card.
Motherboard:GA-945GCM-S2L

---

### Post by sendblink23 on 2010-10-09
woops my bad, got confused, just re-read noticed *ubuntu studio  :P

Well hopefully someone pops in to help... take this as a free bump
---  I have read around you can install regular ubuntu, then afterwards you can convert it to the Studio by installing the packages through a command on terminal.. 
I think it was this: ```
sudo apt-get install ubuntustudio-desktop
```
or
```
sudo apt-get update && sudo apt-get install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video linux-rt
```

---

### Post by amit.kanade1983 on 2010-10-09
@sendblink23 
thanks for your help....but how to do an installation from a dvd....thats my question...:confused:

---

### Post by gordintoronto on 2010-10-09
You left out the most important part of your configuration: Intel 945GC video adapter. I suggest you plug that into Google, perhaps searching on:
ubuntustudio 945gc

---

