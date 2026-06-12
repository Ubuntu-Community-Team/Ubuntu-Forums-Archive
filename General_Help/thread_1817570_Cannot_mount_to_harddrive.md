---
title: "Cannot mount to harddrive"
date: 2011-08-03
forum: General Help
---

### Post by IronArjen on 2011-08-03
I want to save data I have on a partitioned harddisk and I cannot get to the correct part to mount. It is is a long story....

I lost my grub, tried to install from the LiveCD, which only leads me to the terminal....more things that do not work etc etc. So I took out the hard drive put it in another machine and tried to mount it.


*sudo fdisk -l* yields

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18155   145830006    7  HPFS/NTFS
/dev/sda2           18156       36483   147212642+   5  Extended
/dev/sda3           35757       36483     5839596   82  Linux swap / Solaris
/dev/sda5           18156       35036   135588864   83  Linux
/dev/sda6           35037       35756     5782528   82  Linux swap / Solaris

sda1 mounts fine, that&#347; my old windows partition. Then looking at the organization of the other harddrive from I am actually working I deduce that sda5 is my Ubuntu partition.

*sudo mount /dev/sda5 /media/mynewdrive* yields

mount: wrong fs type, bad option, bad superblock on /dev/sda5,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

Then *dmesg | tail* yields


[ 2863.739197]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[ 2863.739213]         19 67 12 13 
[ 2863.739225] sd 1:0:0:0: [sda] Add. Sense: Unrecovered read error - auto reallocate failed
[ 2863.739233] sd 1:0:0:0: [sda] CDB: Read(10): 28 00 19 67 11 c0 00 00 f8 00
[ 2863.739249] end_request: I/O error, dev sda, sector 426185235
[ 2863.739268] JBD: Failed to read block at offset 3906
[ 2863.739283] JBD: recovery failed
[ 2863.739288] EXT4-fs (sda5): error loading journal
[ 2863.739294] ata2: EH complete
[ 2863.739298] 


Total loss? Or is there something I can do?

---

### Post by TeoBigusGeekus on 2011-08-03
Try to search for and correct errors on the drive
```
sudo fsck /dev/sda5
```

---

### Post by IronArjen on 2011-08-03
Yes!, Amazing took three minutes! Thanks a bunch.........

---

### Post by TeoBigusGeekus on 2011-08-03
You're welcome!
Don't forget to mark the thread as solved.

---

