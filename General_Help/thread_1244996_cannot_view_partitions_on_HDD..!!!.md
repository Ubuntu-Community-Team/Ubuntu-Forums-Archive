---
title: "cannot view partitions on HDD..!!!"
date: 2009-08-20
forum: General Help
---

### Post by neophyte_7 on 2009-08-20
I am not able to view the different partitions on the HDD using gparted...

please help someone..!!!!

---

### Post by Bucky Ball on 2009-08-20
What do you see?

---

### Post by neophyte_7 on 2009-08-20
It is displaying that the HDD is single unused partition of 150 GB....!! 

instead of displaying different partitions...

 I am outputting my fdisk -l here...:

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              10        1315    10485760    7  HPFS/NTFS
/dev/sda2   *        1315        9147    62914560    7  HPFS/NTFS
/dev/sda3            9148       19458    82815716    f  W95 Ext'd (LBA)
/dev/sda4   *       19131       19458     2620416    c  W95 FAT32 (LBA)
/dev/sda5            9148        9755     4883728+  83  Linux
/dev/sda6            9756       19130    75302912    7  HPFS/NTFS
/dev/sda7           19131       19458     2620416   dd  Unknown

---

### Post by neophyte_7 on 2009-08-20
How do I post screenshots in the thread..?:(

---

### Post by tgeer43 on 2009-08-20
Yes, by all means at least give us a clue.
If you can't describe it then post a screenshot of gparted.

tgeer

---

### Post by neophyte_7 on 2009-08-20
I am new to this forum, and I dont know I can post the image into the thread....when i click on the image icon, it is requesting a URL..!!

Please help, tgeer43...[IMG]http://ubuntuforums.org/home/madhav/Desktop/Screenshot.png[/IMG]

---

### Post by Bucky Ball on 2009-08-20
If you have more than one drive, are you looking at the right drive in Gparted? There is a tab to the top left to select drives.

---

### Post by neophyte_7 on 2009-08-20
yes....even there, only one single partition is being displayed, /dev/sda(143 GB) :(

also in Gparted>devices> there is only a single partition like this:

Gparted>devices>/dev/sda(143GB)

---

### Post by tgeer43 on 2009-08-20
> **neophyte_7 said:**
> I am new to this forum, and I dont know I can post the image into the thread....when i click on the image icon, it is requesting a URL..!!

Please help, tgeer43...[IMG]http://ubuntuforums.org/home/madhav/Desktop/Screenshot.png[/IMG]
Yes, just upload your screenshot to somewhere on the web like Photobucket or Shutterfly or any of the other many free online photo storage sites and then enter the URL to it in the box after clicking the insert image icon.

tgeer

---

### Post by prshah on 2009-08-20
> **neophyte_7 said:**
> I am not able to view the different partitions on the HDD using gparted.

Run gparted from the command line, and post back messages (if any).

To do this, open a terminal (Applications-Accessories-Terminal) and give the command```
gksudo gparted
```, or if you're using Kubuntu```
kdesudo gparted
```

---

### Post by neophyte_7 on 2009-08-21
Here is the output of gparted from command line...


======================
libparted : 1.7.1
======================
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 read-write (Read-only file system).  /dev/scd0 has been opened read-only.
Unable to open /dev/scd0 - unrecognised disk label.
Can't have overlapping partitions.


something fishy around here..?!
please help.....:)

---

### Post by tgeer43 on 2009-08-22
For whatever reason, gparted is trying to access your CD or DVD drive. With or without a disc in the drive I don't get this message so I'm not sure what's going on.

tgeer

---

