---
title: "Mounting a dd image of a LVM partition"
date: 2010-03-13
forum: General Help
---

### Post by Amirtaker on 2010-03-13
[FONT=Comic Sans MS][SIZE=3]Hi guys,[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]It is the first topic that I have created on this forum, which is related to the mounting of a dd image. I know my question is a genreal question that it will be found by a simple search in search engines but unfortunately, because of the specialty of the creation of this image, and the prblems that brings for me, after nearly five monthes, I decided to tell this problem at this forum.[/SIZE][/FONT]
 
[FONT=Comic Sans MS][SIZE=3]I have a dedicated server that Ubuntu 9.04 operating system has been installed on it. Before this dedicated server, I had another server that according to some reasons, it was put aside and I requested my datacenter support team to attach previous server's HDD to my new server in order to transfer its information to the new server's HDD. On the disks of previous HDD, Ubuntu 8.04 LTS OS had been installed and most of its capacity was full, but while I mounted that HDD on the new server, the contents of the primary partition were visible but the contents of the extended partition weren't visible. After some inspectings, I observerd that the extended partition type is converted to LVM. Before this, I didn't deal with this kind of partition. I tried to mount this partition but I failed. I read many articles about this problem and implemented instructions on the HDD but the LVM partition was never mounted that returns many different errors and even I pursued the reasons of this errors but non of these remedies didn't solve this problem. Since the datacenter had determined a specifies time for transfering information. then I had to return the SCSI HDD on the specified time, so I was forced to make an image of the hard disk by "TestDisk" software. I've made that image from the LVM partition which its capacity amounts to 150 GB but still I'm not able to mount the image according to instructions on the different related websitres. Since I'm really dummy in Linux Fle System field, I request you to help me to mount this image or extract its contents.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3][/SIZE][/FONT] 
[FONT=Comic Sans MS][SIZE=3]I will be grateful to those who can help me.[/SIZE][/FONT]
[FONT=Comic Sans MS][SIZE=3]Thanks[/SIZE][/FONT]

---

### Post by srs5694 on 2010-03-13
First, could you please not specify a font when posting? I find the font you chose hard to read. Thanks.

Second, LVM isn't a file system; it's a system for managing filesystems in structures known as logical volumes rather than in partitions. An LVM partition, if complete, contains logical volumes that can be mounted much like partitions. (Two or more LVM partitions can be linked together to function as one unit.) LVM adds a great deal of flexibility to the layout of systems with multiple filesystems (separate filesystems for /, /home, /opt, and so on), but at the cost of greater complexity.

In order to access your LVM volumes, you must have a kernel compiled with LVM support, and various LVM utilities must be installed and active. I've never heard of LVM being accessed from a file, so I don't know if it will even be possible without your writing that LVM file back out to a partition. You can try, though: Check the contents of the /dev/mapper directory. If you see one file called control, your LVM software is installed but the LVM is not being accessed. If you see other files, the LVM has been detected and you can then mount its filesystems. Chances are you won't find anything. If you do, skip the next paragraph.

Assuming you don't see anything in /dev/mapper but the control file, or if /dev/mapper isn't present at all, you should first check for the LVM utilities. There are several in /sbin, called lvscan, pvscan, vgscan, and so on (they begin with "lv", "vg", or "pv"). If you don't see them, then start by installing the lvm2 package. You must now write your LVM image back out to a real partition. You'll need a big enough partition on your current disk or a spare disk -- it's OK if it's bigger than the source image file, but it must *not* be too small. Using Linux fdisk, change the target partition's type code to 0x8e ("Linux LVM"). When you've done this, copy the image file to the target partition using dd ("dd if=imagefile.img of=/dev/sdb5", changing the filenames as appropriate). You'll probably then need to use the pvscan, vgscan, or lvscan utility, or perhaps reboot. (I don't recall every detail about getting LVMs recognized, but in most cases the bootup scripts do it.) Check again for files in /dev/mapper other than control.

Assuming you can now see files in /dev/mapper, they refer to the filesystem(s) on your original LVM. They could be named anything, but hopefully they'll be descriptive in a useful way (say, foo-home for a /home directory). You can then mount these logical volumes as if they were partitions (as in "mount /dev/mapper/foo-home /mnt") and copy files out of them.

If you still have problems at this point, post back again, along with details of what you see in /dev/mapper, your fdisk -l output, and the output of the pvscan, vgscan, and lvscan commands.

---

