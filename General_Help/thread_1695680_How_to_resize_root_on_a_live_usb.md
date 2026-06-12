---
title: "How to resize root on a live usb?"
date: 2011-02-26
forum: General Help
---

### Post by amoebios on 2011-02-26
i wanted to install updates, but the Update Manager said there wasn't enough space on / although enough free space should be availabe: (see attached screenshot)

Edit:
that is a live USB flash drive, hosting a live system that can be tried  out or installed, that also saves all changes. i just don't get why it  says there's not enough space when clearly there is.

---

### Post by seawolf167 on 2011-02-26
[Here]("http://www.howtoforge.com/partitioning_with_gparted")  [are some]("http://maketecheasier.com/resize-create-partitions-with-gnome-partition-editor-gparted/2009/01/06")  [step]("http://en.kioskea.net/faq/2036-how-to-resize-a-partition-using-gparted-on-linux") by step for using GParted from the LiveCD.

Basically, you'll have to shrink your /home partition (or another partition on the same drive) to give unallocated space, then expand your / partition into the unallocated space.

---

### Post by amoebios on 2011-02-26
Look at the screenshot i posted. The only partitions are /dev/sdc1 and 2 with the mount points /cdrom and /media/16gb2 respectively. Is it even possible to resize partitions that are inside a LiveCD image? :confused:

---

### Post by seawolf167 on 2011-02-26
If you boot from a cd/dvd, that "partition table" would be fixed and you won't be able to resize/move/delete anything (since its already 'hard' written into the physical media). You would, however, be able to resize the 16gb drive (/media/16gb) that is plugged into your computer.

If you want to customize a distro of your own and place it on a cd/dvd there are a number of ways to do that, the first that comes to mind is the [openSUSE Builder]("http://en.opensuse.org//openSUSE:Build_Service")

---

### Post by amoebios on 2011-02-26
My files and applications are being stored correctly and there's enough free space in /tmp. i don't get it....

wait, let me try to explain it: 
that is a live USB flash drive, hosting a live system that can be tried out or installed, that also saves all changes. i just don't get why it says there's not enough space when clearly there is.

---

### Post by amoebios on 2011-03-25
Could it be the FAT32 4 GB limit? Can i spread the image to multiple casper-rw's or would i have to create a partition with a FS that can handle larger files?

---

### Post by amoebios on 2011-03-26
Ha, look, i believe this is how i created this setup:
First, i partitioned the flash drive with another LiveCD i already had. i then used unetbootin to create a LiveUSB on the small partition, then bootet that and used ubuntus Startup Disk Creator to create the persistent system on the larger partition. 
i thought it was booting from the small partition. :P

Let's say i mark the small partition bootable and boot from that, will it save to the other partition? Can't wait to try! :)

---

