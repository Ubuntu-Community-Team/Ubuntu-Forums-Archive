---
title: "Wiped WD Passport 120 GB External Hard Drive"
date: 2011-02-23
forum: General Help
---

### Post by SedukiDude on 2011-02-23
My wife gave me her WD Passport 120 GB external hard drive to use on-the-road and I thought I would erase it clean using the "sudo wipe" command. Well, now I can not use it. Maybe I should have erased individual files instead but I wanted to start clean. 

How do I reformat this thing to work? I looked at the file with "fdisk -l" and it still shows half of the disk is used with 59 out of 120 GB space available.

---

### Post by Kirboosy on 2011-02-23
Try using Gparted (Its in Synaptic Package Manager, System-->Admin-->Synaptic) It will give you a nice GUI to manage your drives/partitions

Make sure you select the external drive and not your OS/internal drive. :)

---

### Post by SedukiDude on 2011-02-23
Okay...will do. Does gparted reformat the disk and erase whatever I have there that is consuming the disk space? Oops! Got to get to work and play with this when I get back.

Thanx,
Kelly

---

### Post by alphaamanitin on 2011-02-23
GParted does not erase what is on the disk besides the disk volume information.  It simply changes the disk volume information and all other "space" on the drive is marked as unused and can be written over.  This is why you can recover files from a drive that has been reformatted with GParted, thank god (personal experience).

If you want to really destroy all data on the drive than I suggest you use the dd command to fill the drive with zeros. 

AlphaA

---

### Post by Kirboosy on 2011-02-23
> **alphaamanitin said:**
> If you want to really destroy all data on the drive than I suggest you use the dd command to fill the drive with zeros. 

This is really not needed but if you feel like you really need to then go for it.

---

### Post by SedukiDude on 2011-04-08
Well now I've wiped out more than I wanted. I can't even see the WD Passport disk when I look in Places. It is like the drive is not even there.

---

