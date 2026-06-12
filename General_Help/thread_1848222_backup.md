---
title: "backup"
date: 2011-09-22
forum: General Help
---

### Post by Artanis.ro on 2011-09-22
I am using ubuntu together with windows 7 in a dual boot environment using grub 2.

I want to create an exact image of the entire hard drive (with both operating systems). Can someone help me?

I want to do it with ubuntu (I find linux more reliable :D), from the live cd, but I don't know how. Maybe you could tell me how to do it from terminal.

Thank you

---

### Post by haqking on 2011-09-22
> **Artanis.ro said:**
> I am using ubuntu together with windows 7 in a dual boot environment using grub 2.

I want to create an exact image of the entire hard drive (with both operating systems). Can someone help me?

I want to do it with ubuntu (I find linux more reliable :D), from the live cd, but I don't know how. Maybe you could tell me how to do it from terminal.

Thank you


[www.clonezilla.org](www.clonezilla.org)

Download and burn .iso then boot system to the CD, clone your chosen partition or disk as an image to another location (external HDD or seperate physical internal disk) then you can clone that image to a location of your choice when you like (make sure target is same size or larger than source.

A good idea before doing this if you have more than one partition is by printing out a copy of your disk utility display, or System monitor file systems tab so that when you are in the Clonezilla interface you know what it is referring to as it can often be confusing when it says things like /dev/sda7 or something similar.

If you have a copy of your disk and partitions to look at you will get by easier.

I prefer to make an image and not clone from one to one directly incase of problems.

Also make sure all partitions are unmounted cleanly before doing so.


Have fun

Regards

haqking

---

### Post by seawolf167 on 2011-09-22
Big +1 for [Clonezilla]("http://www.clonezilla.org"), it'll do everything you want it to do.

---

### Post by Artanis.ro on 2011-09-22
Thank you both for the very useful answers.

Now I have a super heavy question. The reason for me using dual boot environment is because I use the windows at work. Recently it seems that I have to encrypt my hard drive. All good so far. The problem is that 
when I encrypt my drive the grub 2 is inside the MBR and therefore inside the encrypted part of the disk. I don't have any problem with this, however it happened to me that the encrypted software ruined the mbr (once during reset).

And now comes the question :d. Is it possible to restore only the mbr if it gets damaged? I mean to restore it as a image, even if it is encrypted. Maybe if I create a partition just for the mbr? is that possible? The encryption software is Mcafee

10x

---

### Post by seawolf167 on 2011-09-22
You can restore the MBR (Grub2) by following [this guide]("https://help.ubuntu.com/community/Grub2#Reinstalling_GRUB2"). You can also make a separate /boot partition if you'd like too (you won't need it any larger than 500MB). I don't know what encryption software you are using, but with [Truecypt ]("http://www.truecrypt.org/")you shouldn't have any issues.

---

