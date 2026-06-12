---
title: "ext2 -j : Read-only file system ( and lost )"
date: 2011-06-14
forum: General Help
---

### Post by kuifje09 on 2011-06-14
This is very bad,  even in 11.04 ! can't even believe it.  I have an usb disk 40 Gb. And I was loading it with data real fast ( svn ).
At once I could no more write, Read-only file system was reported.
I reckon that problem from years ago on redhat, so I try to fix it.
But It became worse. It was severe damaged.

I created a new filesystem while the disk was out the usb-box and direcly connected to de IDE.  Started all over, and the error also.

Tried to repair with no luck.   It looks like the journal get overrun but i'm not shure.
However i do think its reproduceble. I did it 3 times now and now i am very sick of it.

Please give me some advice to prevent this.

( this is hapening on a updated 10:10 to 11:04 system , a few weeks ago )

---

### Post by kuifje09 on 2011-06-14
I was even thinking my disk was broken.. so I tried another one :

mke2fs -t ext2 -j  -L fsdata /dev/sdc1

mount -t ext3 /dev/sdc1 /media/fsdata
mount: wrong fs type, bad option, bad superblock on /dev/sdc1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

e2fsck -f -y /dev/sdc1
e2fsck 1.41.14 (22-Dec-2010)
e2fsck: Superblock invalid, trying backup blocks...
e2fsck: The ext2 superblock is corrupt while trying to open /dev/sdc1

These commands I can repeat forever so it seems.  Please any advice to solve this.
I am out of my options.o

Now I found this message after a reboot :
[  658.353968] EXT3-fs (sdc1): #blocks per group too big: 2147483648

---

### Post by kuifje09 on 2011-06-15
This was so very wierd, I have been trying those disks on another controler.
I found after a lot of test, for some reason at the one before, my disklabel became destroyed each time.
I connected the disk to another controler and wrote a new label.
Disk is fine now !  even e2fsck -f -n <disk> gave no errors... so nothing to repair.
Maybe a new MoBo.

---

### Post by ubontik on 2011-06-15
I inserted two flash drives. C04D-907E allows to copy files from Documents directory. Flash drive named disk does not allow. They both have the same permissions.

It says: read only file system. It happens on Ubuntu 11.04
$ ls -l /media
                                 drwx------  4 owner owner 16384 1969-12-31 16:00 C04D-907E 
 lrwxrwxrwx  1 root    root        6 2010-10-24 11:41 cdrom -> cdrom0 
 drwxr-xr-x  2 root    root     4096 2010-10-24 11:41 cdrom0 
 drwx------ 12 owner owner 16384 1969-12-31 16:00 disk 



Thanks
I changed file system to FAT32, and it works fine.

---

