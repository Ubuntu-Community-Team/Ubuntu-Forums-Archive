---
title: "Cannot Boot back into Ubuntu/Xp dual boot"
date: 2011-03-09
forum: General Help
---

### Post by Totally on 2011-03-09
Can someone help me here please.

I have windows XP and Ubuntu 10.10. I followed the directions and got this:


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
4 heads, 2 sectors/track, 39072726 cylinders
Units = cylinders of 8 * 512 = 4096 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00047fc9

Device Boot Start End Blocks Id System
/dev/sda1 * 1 6510335 26041339 7 HPFS/NTFS
/dev/sda2 6510336 39072512 130248708 f W95 Ext'd (LBA)
/dev/sda5 6510337 39072512 130248704 83 Linux

Disk /dev/sdb: 3879 MB, 3879731200 bytes
128 heads, 23 sectors/track, 2573 cylinders
Units = cylinders of 2944 * 512 = 1507328 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

Device Boot Start End Blocks Id System
/dev/sdb1 * 1 2574 3788768+ c W95 FAT32 (LBA)
ubuntu@ubuntu:~$ sudomkdir /media/sda5
sudomkdir: command not found
ubuntu@ubuntu:~$ sudo mkdir /media/sda5
ubuntu@ubuntu:~$ sudo mount /dev/sda5 /media/sda5
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/sda5 /dev/sda
/usr/sbin/grub-setup: warn: Your embedding area is unusually small. core.img won't fit in it..
/usr/sbin/grub-setup: warn: Embedding is not possible. GRUB can only be installed in this setup by using blocklists. However, blocklists are UNRELIABLE and their use is discouraged..
/usr/sbin/grub-setup: error: if you really want blocklists, use --force.



What do I do now and how do I get my bootloader to work for xp and ubuntu?

Please help.

---

### Post by oldfred on 2011-03-09
Your hard drive does not  look correct or is it been formated like the new 4K drives? But do not attempt to change anything without good backups.

Disk /dev/sda: 160.0 GB, 160041885696 bytes
[COLOR=Red]4 heads, 2 sectors/track,[/COLOR] 39072726 cylinders
Units = cylinders of 8 * 512 = 4096 bytes

Most LBA drives are set up like mine:
Disk /dev/sda: 160 GB, 160039272960 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312576705 sectors
Units = sectors of 1 * 512 = 512 bytes

What settings do you have in BIOS for hard drive?

---

