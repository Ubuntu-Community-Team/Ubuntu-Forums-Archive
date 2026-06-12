---
title: "ubuntu partition not mounting ,can't enter ubuntu"
date: 2010-04-11
forum: General Help
---

### Post by fasoulas on 2010-04-11
I used a windows program to be able to read the ext3 filesystem from windows but after restarting the computer i can't enter the ubuntu partition it says filesystem faild to mount or something similar.

i then insert the ubuntu live cd because i want some really important files from ext2 ,but when i try to mount the partition it says 

```
Error mounting: mount exited with exit code 32: mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

```

that is the dmesg | tail command output

```

ubuntu@ubuntu:~$ dmesg | tail
[  109.208090]  domain 0: span 0-1 level SIBLING
[  109.208094]   groups: 1 0
[  168.231059] EXT4-fs (sda2): ext4_check_descriptors: Checksum for group 0 failed (29853!=52284)
[  168.231068] EXT4-fs (sda2): group descriptors corrupted!
[  211.783948] EXT4-fs (sda2): ext4_check_descriptors: Checksum for group 0 failed (29853!=52284)
[  211.783956] EXT4-fs (sda2): group descriptors corrupted!
[  632.739866] EXT4-fs (sda2): ext4_check_descriptors: Checksum for group 0 failed (29853!=52284)
[  632.739885] EXT4-fs (sda2): group descriptors corrupted!
[ 1488.233094] EXT4-fs (sda2): ext4_check_descriptors: Checksum for group 0 failed (29853!=52284)
[ 1488.233106] EXT4-fs (sda2): group descriptors corrupted!

```

if anyone can help ,please do so ,
i really need those files and yes i am very stupid for not backing up the files

---

### Post by RudolfMDLT on 2010-04-11
Found this walk through on repairing and restoring a broken superblock:

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

Give it a shot and post back with the results.

Rudolf

---

### Post by fasoulas on 2010-04-11
> **RudolfMDLT said:**
> Found this walk through on repairing and restoring a broken superblock:

[http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/](http://linuxexpresso.wordpress.com/2010/03/31/repair-a-broken-ext4-superblock-in-ubuntu/)

Give it a shot and post back with the results.

Rudolf

ok thanks a lot

that is some more info 

```

ubuntu@ubuntu:~$ sudo fdisk /dev/sda2
Device contains neither a valid DOS partition table, nor Sun, SGI or OSF disklabel
Building a new DOS disklabel with disk identifier 0xb5a0e6d5.
Changes will remain in memory only, until you decide to write them.
After that, of course, the previous content won't be recoverable.


The number of cylinders for this disk is set to 3653.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)
Warning: invalid flag 0x0000 of partition table 4 will be corrected by w(rite)

```

---

### Post by RudolfMDLT on 2010-04-11
Ignore that warning.

this command > sudo fsck.ext4 -v /dev/xxx is the one that'll tell you about your superblock problem.

---

