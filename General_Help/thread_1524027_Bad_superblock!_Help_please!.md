---
title: "Bad superblock! Help please!"
date: 2010-07-04
forum: General Help
---

### Post by Muttley99 on 2010-07-04
Starting Kubuntu 10-04 this morning - attempts to boot with drive activity then hangs.

fdisk -l shows all drives.
started a live CD and ran gparted to check drive - Could not find a valid system superblock!
I have four drives in this computer and I can only access one - the other three are showing bad superblocks!
I tried;

sudo dumpe2fs /dev/sda3 | grep -i superblock

..and I get..

No such file or directory while trying to open /dev/sda3
Couldn't find valid filesystem superblock

backup superblocks are shown only for the good drive - the other three show nothing. 

any help would be much appreciated!!

---

### Post by philinux on 2010-07-04
Run fsck -v /dev/sdxx from the live cd or use system>admin>disk utility

ah kubuntu. Instal palimpsest

---

### Post by Muttley99 on 2010-07-04
My output!

[HTML]root@ubuntu:/# fsck -v /dev/sdd1
fsck from util-linux-ng 2.17.2
e2fsck 1.41.11 (14-Mar-2010)
fsck.ext2: No such file or directory while trying to open /dev/sdd1

The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>[/HTML]

---

### Post by Muttley99 on 2010-07-04
For some reason blkid is showing the following;

[HTML]root@ubuntu:/# blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda: TYPE="nvidia_raid_member" 
/dev/sdc1: LABEL="Volume_3" UUID="bf75f5b3-2f3e-4ad8-8b1a-30dd61351b88" TYPE="ext4" 
/dev/sdd: TYPE="nvidia_raid_member" 
/dev/sdb: TYPE="nvidia_raid_member" 
/dev/mapper/nvidia_dcabdebd1: UUID="a6ecc169-b55a-4826-8c40-3d952bd3f2d8" SEC_TYPE="ext2" TYPE="ext3"[/HTML]

Could this be the reason I can't see the backup superblocks. I would really like to get sda back again as my Kubuntu setup was working perfectly for months.

---

### Post by Muttley99 on 2010-07-04
Well, I abandoned the live CD and tried GParted live instead. I can access my data so some good news.
I still have Kubuntu starting up to a blank blue screen with coloured dots around the top of the screen. This happens in all kernels both in normal and recovery mode. I removed xorg.conf and still the same.
I have an ATI graphics card.

Any ideas appreciated!!

---

