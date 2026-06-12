---
title: "ipod shuffle problem"
date: 2010-01-19
forum: General Help
---

### Post by adampatch on 2010-01-19
**ipod shuffle won't stay mounted** 			
 			 			 		   		 		 		I've been all over looking for a solution to this. It seems plenty of people have similar problems but i've yet to find a solution. I have an ipod shuffle (1st generation, 1GB) and am using a minimal ubuntu 9.10 with xfce4. Previously i had installed xubuntu 9.10 and had the same problem. The ipod doesn't mount automatically and when i mount it manually it unmounts immediately that i try to move anything to or from it.

So:
lsusb knows it's there:

#adam@localhost:~$ lsusb
#Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
#Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
#Bus 004 Device 002: ID 05ac:1301 Apple, Inc. iPod Shuffle 2.Gen
#Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
#Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

as does fdisk but clearly it's not happy with the partition table (i have already buggered this ipod up once trying to solve this problem and used an apple programme to restore it on a windows box so i'm confident that even though linux doesn't like it, this is the partition table as apple intends it.)

#adam@localhost:~$ sudo fdisk -l
#[sudo] password for adam: 

#Disk /dev/sda: 10.1 GB, 10056130560 bytes
#255 heads, 63 sectors/track, 1222 cylinders
#Units = cylinders of 16065 * 512 = 8225280 bytes
#Disk identifier: 0x02530252
#
#   Device Boot      Start         End      Blocks   Id  System
#/dev/sda1   *           1        1178     9462253+  83  Linux
#/dev/sda2            1179        1222      353430    5  Extended
#/dev/sda5            1179        1222      353398+  82  Linux swap / Solaris
#Note: sector size is 2048 (not 512)
#
#Disk /dev/sdc: 1015 MB, 1015021568 bytes
#32 heads, 61 sectors/track, 253 cylinders
#Units = cylinders of 1952 * 2048 = 3997696 bytes
#Disk identifier: 0x6f20736b
#
#This doesn't look like a partition table
#Probably you selected the wrong device.
#
#   Device Boot      Start         End      Blocks   Id  System
#/dev/sdc1   ?      398636      983425  2283019262   72  Unknown
#Partition 1 has different physical/logical beginnings (non-Linux?):
#     phys=(357, 116, 40) logical=(398635, 6, 23)
#Partition 1 has different physical/logical endings:
#     phys=(357, 32, 45) logical=(983424, 30, 61)
#Partition 1 does not end on cylinder boundary.
#/dev/sdc2   ?       86419     1078237  3872056480   65  Novell Netware 386
#Partition 2 has different physical/logical beginnings (non-Linux?):
#     phys=(288, 115, 43) logical=(86418, 26, 1)
#Partition 2 has different physical/logical endings:
#     phys=(367, 114, 50) logical=(1078236, 17, 53)
#Partition 2 does not end on cylinder boundary.
#/dev/sdc3   ?      957932     1949749  3872056384   79  Unknown
#Partition 3 has different physical/logical beginnings (non-Linux?):
#     phys=(366, 32, 33) logical=(957931, 2, 32)
#Partition 3 has different physical/logical endings:
#     phys=(357, 32, 43) logical=(1949748, 25, 36)
#Partition 3 does not end on cylinder boundary.
#/dev/sdc4   ?     1478321     1478349      110998    d  Unknown
#Partition 4 has different physical/logical beginnings (non-Linux?):
#     phys=(372, 97, 50) logical=(1478320, 8, 25)
#Partition 4 has different physical/logical endings:
#     phys=(0, 10, 0) logical=(1478348, 22, 13)
#Partition 4 does not end on cylinder boundary.
#
#Partition table entries are not in disk order
#

all the same i try to mount it and it seems successful 

#adam@localhost:~$ sudo mount -t vfat /dev/sdc/ /media/ipod
#adam@localhost:~$ ls /media/ipod/
#(1979) The Crack                 iPod_Control        rebuild_db.py
#bprea                            rebuild_db.exe
#HAPPY_MONDAYS_PILLS_N_THRILLS_A  rebuild_db.log.txt

but if I try to transfer some files from the ipod, it transfers a few and then:

#adam@localhost:~$ cp -rf /media/ipod/bprea/ /home/adam/
#cp: reading `/media/ipod/bprea/AGEA projet.odp': Input/output error
#cp: cannot stat `/media/ipod/bprea/AGEA projet.pdf': No such file or directory
#cp: cannot stat `/media/ipod/bprea/bprea.doc': No such file or directory
#cp: cannot stat `/media/ipod/bprea/cours fondement bio.odt': No such file or directory
#cp: cannot stat `/media/ipod/bprea/cours ucare plants.odt': No such file or directory

the ipod has now disappeared from /dev/sdc and reappeared on /dev/sdd (this process can be continued ad infinitum, the highest i've been so far while trying out various alternative fixes is /dev/sdi):

#adam@localhost:~$ sudo fdisk -l /dev/sdd
#Note: sector size is 2048 (not 512)
#
#Disk /dev/sdd: 1015 MB, 1015021568 bytes
#32 heads, 61 sectors/track, 253 cylinders
#Units = cylinders of 1952 * 2048 = 3997696 bytes
#Disk identifier: 0x6f20736b
#
#This doesn't look like a partition table
#Probably you selected the wrong device.
#
#   Device Boot      Start         End      Blocks   Id  System
#/dev/sdd1   ?      398636      983425  2283019262   72  Unknown
#Partition 1 has different physical/logical beginnings (non-Linux?):
#     phys=(357, 116, 40) logical=(398635, 6, 23)
#Partition 1 has different physical/logical endings:
#     phys=(357, 32, 45) logical=(983424, 30, 61)
#Partition 1 does not end on cylinder boundary.
#/dev/sdd2   ?       86419     1078237  3872056480   65  Novell Netware 386
#Partition 2 has different physical/logical beginnings (non-Linux?):
#     phys=(288, 115, 43) logical=(86418, 26, 1)
#Partition 2 has different physical/logical endings:
#     phys=(367, 114, 50) logical=(1078236, 17, 53)
#Partition 2 does not end on cylinder boundary.
#/dev/sdd3   ?      957932     1949749  3872056384   79  Unknown
#Partition 3 has different physical/logical beginnings (non-Linux?):
#     phys=(366, 32, 33) logical=(957931, 2, 32)
#Partition 3 has different physical/logical endings:
#     phys=(357, 32, 43) logical=(1949748, 25, 36)
#Partition 3 does not end on cylinder boundary.
#/dev/sdd4   ?     1478321     1478349      110998    d  Unknown
#Partition 4 has different physical/logical beginnings (non-Linux?):
#     phys=(372, 97, 50) logical=(1478320, 8, 25)
#Partition 4 has different physical/logical endings:
#     phys=(0, 10, 0) logical=(1478348, 22, 13)
#Partition 4 does not end on cylinder boundary.
#
#Partition table entries are not in disk order
#

I've tried installing various different mount utilities (pmount, pymount etc as well as seeing if gtkpod could see it) all to no avail. The message in fdisk "Note: sector size is 2048 (not 512)" led me to try reformatting the drive with fdisk but that did no good. I attach my ipod via a pcmcia usb2.0 hub (there's no working usb port on my laptop). The hub works fine with other usb devices. I've tried various things suggested on various websites (mainly this one) and am now at a complete loss. Anyone have any idea what the problem is?

---

### Post by vamega on 2010-01-19
I'm not really sure what to make of this.
Perhaps you could try this on another linux machine if possible, and see if it happens there as well.

Vamega

---

### Post by adampatch on 2010-01-19
that might be difficult, i've only got one laptop and i'm the only linux user i know... On the other hand, i did try one or two live cd installations recently such as damn small linux, puppy, tinyme... and it worked with some of those  (i don't remember which). It was also working on this laptop when it was running XP.

---

