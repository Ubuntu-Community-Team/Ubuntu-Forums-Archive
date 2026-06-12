---
title: "Odd issue with mounting an NTFS drive"
date: 2010-11-28
forum: General Help
---

### Post by politenessman on 2010-11-28
I am running xubuntu 10.04
I have an NTFS partition that I share with Win 7, and I want to mount it to the desktop. I've done a little searching and worked out how to mount the drive, but alas I don't seem to be able to see it on my desktop,

Here is my fstab file:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda5 :
UUID=8cf29826-b183-4547-8be4-07c4566ed1ef	/	ext2	errors=remount-ro	0	1
#Entry for /dev/sda7 :
UUID=2142e365-acde-4b50-8f48-0001e0722e8e	/home	ext4	defaults	02
#Entry for /dev/sda2 :
UUID=72AA1FACAA1F6C3B	/media/Acer	ntfs-3g	defaults,locale=en_US.utf8	00
#Entry for /dev/sda1 :
UUID=6E429D19429CE75D	/media/PQSERVICE	ntfs-3g	defaults,locale=en_US.utf8	0	0
#Entry for /dev/sda4 :
UUID=7C5330D86C5B0C85	/media/data	ntfs-3g	defaults,locale=en_US.utf8	00
#Entry for /dev/sda6 :
UUID=64795171-3907-4c4f-87cc-23b8a925b8c4	none	swap	sw	0	0
/dev/scd0	/media/floppy0	auto	rw,user,noauto,exec,utf8	0	0


The drive in question is sda4 - I can see it if I navigate to /media/data, but it doesn't appear on my desktop (same for /media/PQSERVICE but that is ok, I don't want that drive on my desktop). 
I seem to have two instances of my CD drive on my desktop, and I'm not sure why that is. 

Anyone have any wisdom or thoughts?

---

### Post by linux-hack on 2010-11-28
If you mount you windows drive on /media/data its normal that is not on your desktop.

You should change the mounting point on your desktop... or simply make a symbolik link...

---

### Post by politenessman on 2010-11-28
I see. So I went back and edited the fstab file thus:

proc                                       /proc                proc     nodev,noexec,nosuid         0  0  
UUID=8cf29826-b183-4547-8be4-07c4566ed1ef  /                    ext2     errors=remount-ro           0  1  
UUID=2142e365-acde-4b50-8f48-0001e0722e8e  /home                ext4     defaults                    0  2  
UUID=72AA1FACAA1F6C3B                      /media/Acer          ntfs-3g  defaults,locale=en_US.utf8  0  0  
UUID=6E429D19429CE75D                      /media/PQSERVICE     ntfs-3g  defaults,locale=en_US.utf8  0  0  
UUID=7C5330D86C5B0C85                      /home/tonyp/Desktop  ntfs-3g  defaults,locale=en_US.utf8  0  0  
UUID=64795171-3907-4c4f-87cc-23b8a925b8c4  none                 swap     sw                          0  0  
/dev/scd0                                  /media/floppy0       auto     rw,user,noauto,exec,utf8    0  0  

I still see two copies of my CD drive, and no data drive.
Any further thoughts?

---

### Post by politenessman on 2010-11-28
I wonder if it is a permissions problem?

When the drive location is set to /media/data I can see my data on the drive and read files just fine (I haven't tried writing anything yet)

When set to /home/tonyp/Desktop I can't see any of my files or folders.

---

### Post by politenessman on 2010-12-09
I solved the problem by reformatting the drive as a FAT32 drive, thus eliminating any permissions issues.
Once that was done, and the fstab file modified, everything worked as it should.

---

