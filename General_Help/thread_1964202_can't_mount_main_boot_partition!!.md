---
title: "can't mount main boot partition!!"
date: 2012-04-23
forum: General Help
---

### Post by petermg on 2012-04-23
After many failed boot attempts I booted off a live 11.10 CD.  The first partition is my main Ubuntu 11.10 EXT3 partition, but I also have an NTFS partition on the same physical drive.  I can mount the NTFS partition and see the files fine but cannot the main boot EXT3 partition.  This is what I get when trying to mount the main partition


```
Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sda1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

And so when I try "dmesg | tail" I get
```
[  274.484351]         72 03 11 04 00 00 00 0c 00 0a 80 00 00 00 00 00 
[  274.484362]         02 34 26 3e 
[  274.484366] sd 0:0:0:0: [sda]  Add. Sense: Unrecovered read error - auto reallocate failed
[  274.484373] sd 0:0:0:0: [sda] CDB: Read(10): 28 00 02 34 26 38 00 00 08 00
[  274.484384] end_request: I/O error, dev sda, sector 36972094
[  274.484412] ata1: EH complete
[  274.484435] JBD: Failed to read block at offset 452
[  274.484438] JBD: IO error -5 recovering block 452 in log
[  274.502526] JBD: recovery failed
[  274.502533] EXT3-fs (sda1): error loading journal
```


I am totally lost!  I have a bunch of photos and videos of my family on that partition and those files are my main concern to recover.  Any help is appreciated!!  Thank you.

---

### Post by oldfred on 2012-04-23
I might try this first:

#From liveCD so everything is unmounted,swap off if necessary, change example with sda1 to your partition(s) if you have more than sda1 with ext3 format.
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

---

### Post by petermg on 2012-04-23
> **oldfred said:**
> I might try this first:

#From liveCD so everything is unmounted,swap off if necessary, change example with sda1 to your partition(s) if you have more than sda1 with ext3 format.
#e2fsck is used to check the ext2/ext3/ext4 family of file systems.
sudo e2fsck -C0 -p -f -v /dev/sda1
#if errors:
sudo e2fsck -f -y -v /dev/sda1

oldfred THANK YOU!!!! I LOVE YOU!!!!!!!!!!!!!!  That totally worked!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!! !!!!!!!!!!!!!!!!!!!!!!!!!!!!!! !!!!!!!!!!!!!!!!!!!!!!!!!!!!! WOOOOOOOHOOOOOOOOO!!!!!!!!!!!!!!!!
:guitar:
:popcorn:
:KS:KS:KS
:biggrin:\\:D/

---

