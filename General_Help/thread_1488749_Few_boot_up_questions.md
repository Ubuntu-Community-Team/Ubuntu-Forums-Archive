---
title: "Few boot up questions"
date: 2010-05-20
forum: General Help
---

### Post by Disparition on 2010-05-20
I've got few questions about the 10.04 release and some in general.

1) I've got a 500GB harddisk with 5 partitions, equally divided in size. The main one has Windows 7 and Ubuntu installed. When I try to use the other partitions, it asks for a password. Password is no big deal, but it places a shortcut for those disks on the desktop. Is there a way to prevent Ubuntu from placing these shortcuts. 

2) Is there a way to change the boot list order so It boots ubuntu without me selecting which one to boot?

I'd really appreciate your help :)

---

### Post by dino99 on 2010-05-20
install mountmanager with synaptic and set your prefs with it (system admin mountmanager)

---

### Post by Disparition on 2010-05-20
> **dino99 said:**
> install mountmanager with synaptic and set your prefs with it (system admin mountmanager)

Thanks a lot. Does this apply for both of my questions?

---

### Post by philinux on 2010-05-20
The app startupmanager is an easy way to do your second request

---

### Post by SlidingHorn on 2010-05-20
> **Disparition said:**
> I've got few questions about the 10.04 release and some in general.

1) I've got a 500GB harddisk with 5 partitions, equally divided in size. The main one has Windows 7 and Ubuntu installed. When I try to use the other partitions, it asks for a password. Password is no big deal, but it places a shortcut for those disks on the desktop. Is there a way to prevent Ubuntu from placing these shortcuts. 

This thread's a little old, but I think it should still be valid for your purposes: [http://ubuntuforums.org/showthread.php?t=125397]("http://ubuntuforums.org/showthread.php?t=125397")

> **Disparition said:**
> 2) Is there a way to change the boot list order so It boots ubuntu without me selecting which one to boot?

Here's a tutorial that shows you how to do this.  Pretty straight forward, but let us know if you have any issues:  [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

---

### Post by metalf8801 on 2010-05-20
I can help you with question 2 
You can use StartUp Manager to edit your Grub menu
System > Administration > StartUp-Manager 

You might need to use the Ubuntu Software Center to install it if you don't see StartUp-Manager in the Systems menu 

I hope that helps 
Dan

---

### Post by dino99 on 2010-05-20
> **Disparition said:**
> Thanks a lot. Does this apply for both of my questions?

goto system admin bootup-manager and select which kernel you want to boot on

---

### Post by Disparition on 2010-05-20
Thanks alot!

---

### Post by philinux on 2010-05-20
> **SlidingHorn said:**
> Here's a tutorial that shows you how to do this.  Pretty straight forward, but let us know if you have any issues:  [https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS]("https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS")

Thats for legacy grub not grub2 ;)

---

### Post by SlidingHorn on 2010-05-20
> **philinux said:**
> Thats for legacy grub not grub2 ;)

+1 nice catch --  I suck @ this job

---

