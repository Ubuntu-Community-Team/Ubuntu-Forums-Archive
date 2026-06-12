---
title: "USB problem"
date: 2010-08-27
forum: General Help
---

### Post by Kajmak on 2010-08-27
Hello, I'm having problem with detecting my usb on ubuntu. Few days ago i was removing some stuff on my virtual box and after that my ubuntu just stopped reading my usb. I also tried plugging it in some computers with windows OS and it did recognized USB device but it couldn't open nor tell its name and capacity, i also tried formatting the device on windows but it didnt let me. 

Anyone has any solution to this problem? 
Thanks in advance!

---

### Post by dineshs on 2010-08-27
Switch ON your PC after plugging in the device
Does it detect?

---

### Post by Ravenheart on 2010-08-27
If you type **lsusb** in the terminal what do you get?  What version of Ubuntu are you using?

---

### Post by Kajmak on 2010-08-27
It doesn't detect it, when i did lsusb with usb plugged in it gave me "Bus 001 Device 006: ID 0930:6545 Toshiba Corp. Kingston DataTraveler 2.0 Stick (4GB) / PNY Attache 4GB Stick
"
after i plugged it off and did the same command, it didnt show me anything. 
Well ofc it didn't showed me anything, but why am i writing this is because my USB is 16 gb or well (14.9) and it showed 4GB stick???

I used 10.04 version of ubuntu.

---

### Post by TwoEars on 2010-08-27
If that is indeed the case, then perhaps you've been sold a fake USB stick. Where did you buy it from?
Are you certain that it is meant to be 16GBs?

---

### Post by Kajmak on 2010-08-27
Yes ofc, I've been using that usb for 1 year now.

Although i had 4 gb usb plugged in like 3 hours ago, maybe its reading that former usb when i plugg in mine, because mine doesn't have an 
"ID"

---

### Post by Grenage on 2010-08-27
They all have IDs.

If you can't get it working in a windows OR Ubuntu machine, I'd imagine it's died.  You can try to fdisk it from a console, to delete and recreate the partition.  Then format it.

---

### Post by Kajmak on 2010-08-27
well windows can detect it, it shows Removable disc, but i cant format it.


How should i do that what u suggested, do that in windows perhaps?

---

### Post by Grenage on 2010-08-27
I don't know about windows, but what I've done in Linux before:

Without the drive plugged it:

```
sudo fdisk -l
```

Then with the drive plugged in:

```
sudo fdisk -l
```

Spot the difference!  A new drive should have appeared (sda, sdb, etc), possibly with partitions (sda1, sda2).  Note that you likely already have sda or hda as you main hard drive.  Let's assume the USB key is sdd).

With the drive identified, partition it (the drive, not the partition):

```
sudo fdisk /dev/sdd
```

The menu lists possible commands.  You'll want to delete any existing partitions, then create a new partition.  When you've created it, I'd recommend changing the type to FAT32, which I think is type *c*.  You'd then exit, saving changes with the *w* key.

Now you want to format the partition (not the drive):

```
sudo mkdosfs -F 32 /dev/sdd1
```

Hopefully, that helped; be sure to double-check any commands you type - you don't want to format or delete the partition on the wrong disc.

---

### Post by Ravenheart on 2010-08-27
Ok.  If **lsusb** detects it, it probably means that the stick is ok.  I wouldn't sweat the 4Gb label - I've seen stuff like that before on sticks which were 8Gb and bigger.  I had a similar problem a while back while using virtualbox where I fiddled with the settings for the stick to allow virtualbox to read and write to it but afterwards it wouldn't mount.  The stick was formatted in **vfat** and I had inadvertently change the umask to prevent anybody reading or writing to it(or any other vfat formatted device for this matter!!).  I used the configuration editor to do this (while using 9.04), however there does not appear to be access to this in 10.04.

Can you see the disk in the Disk Utility?
System > Administration > Disk Utility

---

### Post by Kajmak on 2010-08-27
Success! What i did was, i went on windows, My computer, manage, found disk, my usb was marked as Blank (unallocated) i pressed right click on it and choose wizard to configure that, i just followed a few steppes and it worked like a charm!

Big thanks to everyone for their posts and efforts!

---

### Post by Grenage on 2010-08-27
As suspected, a corrupt partition table.

Glad you got it sorted.

---

