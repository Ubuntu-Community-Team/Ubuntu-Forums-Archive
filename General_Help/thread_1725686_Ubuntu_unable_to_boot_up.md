---
title: "Ubuntu unable to boot up"
date: 2011-04-10
forum: General Help
---

### Post by fnota on 2011-04-10
Recently i downloaded this application, EasyBCD from Neosmart to fix my one of my partition. However i accidentally reset the BCD configuration, which reset all my entries. 
So all my entries were gone.
I restore my window 7 bootloader using it window 7 recovery disk.
But i am unable to restore ubuntu bootloader. 
I try to manually key in ubuntu entry 
Type: Grub 2
Name: Neosmart Linux
Device automatically configured
I added the entry and reboot.
However when i try to boot Neosmart Linux,
it bring me to a black screen with many grub stuff there.
I uploaded a screenshot below

---

### Post by earthpigg on 2011-04-10
> **fnota said:**
> 
I try to manually key in ubuntu entry 
Type: Grub 2
Name: Neosmart Linux
Device automatically configured
I added the entry and reboot.
However when i try to boot Neosmart Linux,
it bring me to a black screen with many grub stuff there.
I uploaded a screenshot below

it kind of looks like you are using a set of directions from grub1 - ubuntu now uses grub2. make sure you are using a guide that is for 10.04 or later.

and: i have no idea what neosmart linux is. you will need to figure out if it uses grub1 or grub2...

---

### Post by fnota on 2011-04-10
actually neosmart linux = ubuntu , because i sort of rename it. I am using ubuntu 10.04

---

