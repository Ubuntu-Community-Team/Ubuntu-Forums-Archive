---
title: "run wubi in a VM"
date: 2010-12-23
forum: General Help
---

### Post by larryboyadm on 2010-12-23
I am wondering if it is possible to run my existing wubi install inside of a VM while i am logged into windows. Has anyone else tried to do this or is it even possible to do?

---

### Post by mlentink on 2010-12-23
Why would you?
- Back-up your files (/home directory)
- Start up VirtualBox
- Install Ubuntu
- Restore your files

Wubi installs Ubuntu as a virtual **drive** (as opposed to virtual machine) in a windows file. There's absolutely no need to copy that to a virtual machine. You can install Ubuntu natively into that virtual machine.

---

### Post by larryboyadm on 2010-12-23
That would double the amount of HDD space that i am using for  wubi. I still want to be able to boot into Ubuntu (i spend most of my time in Ubuntu and just boot up to windows when i need to.) I just want to access any files or programs in wubi if i have to get onto windows.

> **mlentink said:**
> 
Wubi installs Ubuntu as a virtual **drive** (as opposed to virtual machine) in a windows file. There's absolutely no need to copy that to a virtual machine. You can install Ubuntu natively into that virtual machine.

---

### Post by bcbc on 2010-12-23
[[wubi] Virtualbox to Boot Wubi inside Windows]("http://ubuntuforums.org/showthread.php?t=1232698")

Never done it myself, but apparently community member *horse_dung* has figured it out.

---

### Post by larryboyadm on 2010-12-23
> **bcbc said:**
> [[wubi] Virtualbox to Boot Wubi inside Windows]("http://ubuntuforums.org/showthread.php?t=1232698")

Never done it myself, but apparently community member *horse_dung* has figured it out.

Thank you. Looks like this is exactly what i was looking for. Will mark thread as solved when I have it working.

---

### Post by larryboyadm on 2010-12-23
Ok so the link needed to download the files to make it work seems to be down. I think i know basically what he did to get it working and i will keep trying. If anyone knows a working way to do this with 10.10 it would be greatly appreciated.

---

### Post by bcbc on 2010-12-23
> **larryboyadm said:**
> Ok so the link needed to download the files to make it work seems to be down. I think i know basically what he did to get it working and i will keep trying. If anyone knows a working way to do this with 10.10 it would be greatly appreciated.

Why don't you post in that thread - probably *horse_dung* is subscribed to it, or someone else who got it working will respond.

---

### Post by larryboyadm on 2010-12-30
I have tried a few things and haven't had any luck with this so far. I am a noob when it comes to virtualization but this is something i have been working on for a while now. It seems horse dung has not logged in for about 6 months so if anyone else has any ideas to get this to work it will be greatly appreciated

---

