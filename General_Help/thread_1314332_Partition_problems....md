---
title: "Partition problems..."
date: 2009-11-04
forum: General Help
---

### Post by yorkshireflatcap on 2009-11-04
All, 

If I unmount a partition in GParted and removed all partitions, does this mean that I have lost everything, including the partition that I've just unmounted?

Many Thanks

John

---

### Post by coffeecat on 2009-11-04
If you clicked on Apply then then answer is yes. Apply is the big green tick in the version that comes with Karmic. If you didn't click on Apply then no, but if you quit Gparted it will prompt you that you haven't actioned your changes.

Can you give more details?

---

### Post by ezsit on 2009-11-04
If you have committed the changes to disk, then yes, you have deleted the old partition you previous unmounted. However, if you have not done ANYTHING else to the disk, re-creating the exact partitions with **cfdisk** may allow you to access those partitions again. 

I stress, do not use gparted to re-create the partitions because gparted will format the partitions when it creates them. **cfdisk** will not format the partitions, it will only re-write the master boot record containing the partition information. Make sure to re-create the partitions EXACTLY as they were. 

Another option might be to use a program called testdisk, but please do some research on your own before using testdisk as it can be an involved process.

BTW, **cfdisk** is a command line program, so invoke in a terminal:

sudo cfdisk /dev/sdb

/dev/sdb is just an example, you must supply the correct device for cfdisk to open and the device must not be mounted nor have an active swap partition.

---

### Post by yorkshireflatcap on 2009-11-04
The only details I can give is that the partition that I wanted to keep, I just unmounted and it disappeared from the list assuming that anything done in GParted will not affect the unmounted partition.

I first selected the partition I wanted to keep and selected the Unmount option in GParted.  I then selected all the partitions that I wanted to remove.... I pressed deleted and it asked me if I'm sure, I pressed yes.

But when I go into file explorer, I can see it but can't access it!!

is there some chance that I can recover the files.... they're all my piccies dating back to 2004!!!!!

regards

Yorki

---

### Post by ezsit on 2009-11-04
Is this an external drive? If so, since the partition in unmounted, unplug it and replug it in. See if the partition is still there and automounts when replugged into the computer.

---

### Post by yorkshireflatcap on 2009-11-04
> **ezsit said:**
> Is this an external drive? If so, since the partition in unmounted, unplug it and replug it in. See if the partition is still there and automounts when replugged into the computer.

I'm afraid its not an external HDD, it was on my main HDD...  Surely there must be a way to recover lost files.... at the mo I am looking at testdisk utility.

Regards

Yorki

---

### Post by coffeecat on 2009-11-04
It is just possible that your partition is not deleted, but that because of changes to the partition table, udev (or whatever does the mounting - with all the changes over the years I've forgotten) is confused. Which may be why you can see it but not mount it. A simple restart of the relevant services may be needed. The easiest way would be a reboot. Then try to mount from the Places menu, before you try anything like testdisk.

---

### Post by yorkshireflatcap on 2009-11-05
Hi Coffeecat....

Just thought I'd let you know of my progress.  I managed to retrieve *all* my files from the deleted partition.  I just used testdisk and followed the instructions.  Its a very simple but powerful utility.

Cheers

Yorki

---

