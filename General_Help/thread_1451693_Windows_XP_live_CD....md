---
title: "Windows XP live CD..."
date: 2010-04-10
forum: General Help
---

### Post by WiReIs on 2010-04-10
Hi, im running ubuntu 9.10 as my OS on my laptop, i have a copy of windows xp pro and would rather not install a partition.. So i was wondering if it was possible to convert the XP pro install cd to an .ISO image file so i can run windows XP on a virtual machine (virtualbox) if so how do i go about this? I have installed k3b to actually burn the ISO image to a CD but im unsure of a program that can convert the xp to ISO, any help would be greatly appreciated as im quite new to linux :) many thanks, Ross

---

### Post by blueridgedog on 2010-04-10
Why not simply mount the ISO in virtual box and tell it to boot.  It should start the windows install into the virtual machine you have created.

---

### Post by lisati on 2010-04-10
I'm not overly experienced in such matters, but suspect that one option might be to start virtualbox, then direct it to run the setup from the CD.

---

### Post by WiReIs on 2010-04-10
when i run xp in the virtual machine it asks me to install or create partition.. 

is it not possible to convert the xp files into an iso file to boot as a live cd as i havent much space for another os on my laptop

---

### Post by marshmallow1304 on 2010-04-10
The Windows CD, unlike many Linux CDs, is not Live.  It must be installed to run Windows.  Installing in Virtualbox does not change the partitions of your actual hard drive.  It just partitions a virtual hard drive which is contained within a file on your real hard drive.

---

### Post by blueridgedog on 2010-04-10
> **WiReIs said:**
> when i run xp in the virtual machine it asks me to install or create partition.. 

is it not possible to convert the xp files into an iso file to boot as a live cd as i havent much space for another os on my laptop

You could install the virtual machine on a USB flash drive, so you could avoid the need for space, but sadly there is no way to have a live windows CD.

---

### Post by WiReIs on 2010-04-10
ok :) thanks for help guys

---

