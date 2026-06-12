---
title: "Some questions about UBUNTU"
date: 2009-12-21
forum: General Help
---

### Post by guitarrarl on 2009-12-21
Hi friends:

I run Ubunto 9.10 on my hp-mini 10nr installed on a 16 Gig SD card. It runs great. I have the following questions about Ubuntu:

1-Installing Ubuntu from a DVD only wants to install to the internal C:drive, Is it possible to do an install from the Ubuntu desktop to an external drive? I want to install it for a friend on his USB external HD.

2-I copied the complete Ubuntu folder from my SD to an external drive but when booting if says "you must run the kernel fisrt" Why it can not load from the same data contained on the working SD folder?

3-Where can I find good tutorial about how to create an Iso Live CD from Remastersys? I have it installed and it runs well.

I was able to install Ubunto to the SD from the Windows xp desktop using Wubi and it downloaded the files from online. Is it possible to use the downloaded files to do a second install? On each install it wants to download again the files!

Thanks for your help amigos :P

Raymond 

[http://www.afn.org/~guitarra/]("http://www.afn.org/%7Eguitarra/")

---

### Post by gordintoronto on 2009-12-21
Issue 16 of Full Circle Magazine talks about Remastersys.

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

Re Q1: do you want to install to your friend's USB hard drive on your machine?  This might cause trouble unless the two of you have identical hardware.

---

### Post by blueridgedog on 2009-12-21
> **guitarrarl said:**
> 1-Installing Ubuntu from a DVD only wants to install to the internal C:drive, Is it possible to do an install from the Ubuntu desktop to an external drive? I want to install it for a friend on his USB external HD.


If the drive or media is installed/plugged in when the system boots, it should allow you to install to it.  If not, post back and we can troubleshoot it.

---

### Post by guitarrarl on 2009-12-22
Hi friend: I would like to install to an SD, his machine is different but I have the original Ubuntu 9.10 image. It only wants to install to his internal C: drive not the SD or esternal HD.

Thanks!
RL

> **gordintoronto said:**
> Issue 16 of Full Circle Magazine talks about Remastersys.

[http://fullcirclemagazine.org/](http://fullcirclemagazine.org/)

Re Q1: do you want to install to your friend's USB hard drive on your machine?  This might cause trouble unless the two of you have identical hardware.

---

### Post by 3rdalbum on 2009-12-22
You can probably use the 'manual' partitioning method to install to the external hard drive.

After that, on the screen that confirms what you have asked it to do, there is an Advanced button click this and then in the space where you can specify a location to install a bootloader, you need to type the device file name for the external hard drive.

This should look like '/dev/sdb'.

---

