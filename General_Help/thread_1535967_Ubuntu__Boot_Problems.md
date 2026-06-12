---
title: "Ubuntu  Boot Problems"
date: 2010-07-21
forum: General Help
---

### Post by Tobelli on 2010-07-21
Dear Ubuntu Community!

I love Ubuntu and never had any problems with it, but recently I have been having problems during the boot procedure.

I am running Ubuntu 10.04 64bit on an Acer Aspire 5741 Notebook.

A FEW DAYS AGO
when I switched the laptop on the following message showed up:
```

DRY ERR
Status dry err
Errors where found while checking the  disk for boot.

F to attempt to fix errors....

```
I was able to log in pressing F 
Checking the boot log report in the System protocoll the following showed up:

```

fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
fsck from util-linux-ng 2.17.2 
/dev/sda1: clean, 221053/2454192 files, 1341008/9797632 blocks (check in 3 mounts) 
Error reading block 139265 (Attempt to read block from filesystem resulted in short read).  

/dev/sda6: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY. 
	(i.e., without -a or -p options) 
mountall: fsck /boot [436] terminated with status 4 
mountall: Filesystem has errors: /boot 
/dev/sda5: clean, 22896/36012032 files, 27259505/144042752 blocks 
init: ureadahead-other main process (943) terminated with status 4 

Attempting to fix /boot filesystem 
fsck from util-linux-ng 2.17.2 
e2fsck 1.41.11 (14-Mar-2010) 
Error reading block 139265 (Attempt to read block from filesystem resulted in short read).  Ignore error? yes 

Force rewrite? yes 

Superblock has an invalid journal (inode 8). 
Clear? yes 

*** ext3 journal has been deleted - filesystem is now ext2 only *** 

Superblock has_journal flag is clear, but a journal inode is present. 
Clear? yes 

/dev/sda6 contains a file system with errors, check forced. 
Pass 1: Checking inodes, blocks, and sizes 
Journal inode is not in use, but contains data.  Clear? yes 

Pass 2: Checking directory structure 
Pass 3: Checking directory connectivity 
Pass 4: Checking reference counts 
Pass 5: Checking group summary information 
Block bitmap differences:  -(139265--147456) 
Fix? yes 

Free blocks count wrong for group #17 (0, counted=8192). 
Fix? yes 

Free blocks count wrong (397576, counted=405768). 
Fix? yes 

Recreate journal? yes 

Creating journal (8192 blocks):  Done. 

*** journal has been re-created - filesystem is now ext3 again *** 

/dev/sda6: ***** FILE SYSTEM WAS MODIFIED ***** 
/dev/sda6: 223/121920 files (1.3% non-contiguous), 89848/487424 blocks 
mountall: fsck /boot [944] terminated with status 1 
 * Starting AppArmor profiles       #[80G Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox 

#[74G[ OK ] 
 * Setting sensors limits       #[80G 
#[74G[ OK ] 

```
I deleted some libraries I had recently installed and the error message during the booting disappeared.




NOW
,at the moment, however I experience another error message at the boot up:
```

Gave up waiting for a root device. Common problems:

check rootdelay =  (did the system wait long enough?)
Check root = (did the system wait for the right device?)
missing modules (cat  /proc/modules;  ls/dev)

Alert!   dev/disk/by-uuid/feb9d78-898989-......   does not exist

```
After this error message ubuntu starts a shell and I type in „reboot“ and everything works fine from there (a part from the long booting*)

Unfortunately I do not have enough Computer knowledge to understand the above stated error messages.

I was hoping you could help me out fixing this problem.




*Also what I was experiencing was a way longer boot time, especially after doing the login. Usually it took just 5 seconds at the most for the system to be ready, but now I need to wait about 30seconds or even more (these are Windows times :D).

---

### Post by Rubi1200 on 2010-07-21
Hi,
could you please post the output from:

```
sudo fdisk -l
```

and

```
sudo blkid
```

Run the commands one at a time in a terminal.

---

### Post by Tobelli on 2010-07-22
Hello!

The outputs:

Fdisk:
```
Platte /dev/sda: 640.1 GByte, 640135028736 Byte
255 Köpfe, 63 Sektoren/Spur, 77825 Zylinder
Einheiten = Zylinder von 16065 × 512 = 8225280 Bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e768e

   Gerät  boot.     Anfang        Ende     Blöcke   Id  System
/dev/sda1   *           1        4880    39192576   83  Linux
/dev/sda2            4880       77826   585936897    5  Erweiterte
/dev/sda5            4880       76610   576171008   83  Linux
/dev/sda6           76610       76671      487424   83  Linux
/dev/sda7           76671       77826     9276416   82  Linux Swap / Solaris
```

sudo blkid
```
/dev/sda1: UUID="febb9d78-806e-488f-b2ab-2f08c3bd51b6" TYPE="ext4" 
/dev/sda5: UUID="72e710a8-35dc-43d9-9185-e4f150c7f0fd" TYPE="ext4" 
/dev/sda6: UUID="869fb7ae-cad7-4615-9d6e-8bc8091ded58" TYPE="ext4" 
/dev/sda7: UUID="134c35f3-1db3-4ebe-86bb-429410534d79" TYPE="swap" 
/dev/sdb1: LABEL="TOBELLI" UUID="13F7-363C" TYPE="vfat" 

```

---

### Post by Tobelli on 2010-07-27
Since nobody seems to be knowledgeable about my issue, perhaps we could address it in another way.

Do you have any tipps on how to speed up the boot process? Especially after the login?

Thank you very much indeed

---

