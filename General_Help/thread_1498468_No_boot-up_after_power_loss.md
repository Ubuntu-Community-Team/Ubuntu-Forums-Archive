---
title: "No boot-up after power loss"
date: 2010-05-31
forum: General Help
---

### Post by rduch on 2010-05-31
Ubuntu 10.4 on desktop system. Everything was working satisfactorily until...

Trying to boot up after a power loss I got 
"ERROR: You need to load the kernel first."

I tried to boot into recovery mode and got 
"ERROR: HD0, 1 out of disk
 ERROR: Couldn't read file Loading initial ramdisk
 ERROR: You need to load the kernel first."

Next I booted with the live Ubuntu disk to see if I could mount the drive from there and got this

Error mounting: mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

dmesg | tail  returned this
ubuntu@ubuntu:~$ dmesg | tail
[ 1280.344490] sd 4:0:0:0: [sdb] Add. Sense: No additional sense information
[ 1280.344497] sd 4:0:0:0: [sdb] CDB: Read(10): 28 00 05 cc c8 af 00 01 00 00
[ 1280.344510] end_request: I/O error, dev sdb, sector 97306799
[ 1280.344566] ata4: EH complete
[ 1280.344596] JBD: Failed to read block at offset 5893
[ 1280.344610] JBD: recovery failed
[ 1280.344613] EXT3-fs: error loading journal.
[ 1280.384056] kjournald starting.  Commit interval 5 seconds
[ 1280.384313] EXT3 FS on sdb6, internal journal
[ 1280.384322] EXT3-fs: mounted filesystem with ordered data mode.

The physical drive is divided into 3 virtual drives. The partition with the operating system will not boot, but the other two drives will mount normally with live Ubuntu.

My guess is that the boot sector and/or files are corrupted. Can this drive be recovered with a repair or do I need to re-load the OS and start from scratch. I need to minimize my downtime on this.

Any help is appreciated.

---

### Post by lmarmisa on 2010-05-31
Try to fix the damaged partition with fsck:

> 
sudo fsck /dev/sdb1



Gparted is another tool that can help you to diagnose the problem.

---

### Post by gentoo4810tzg on 2010-06-23
**EDIT: I am not sure if this actually works**

I had something similar with my 10.04 LTS. The following worked for me, so it might be a solution:

Edit the file */etc/default/grub*: Let ***GRUB_DISABLE_LINUX_UUID="true"*** be uncommented, eg. present.
(You can use a live CD to mount the partition, to get access to the file)


References:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

