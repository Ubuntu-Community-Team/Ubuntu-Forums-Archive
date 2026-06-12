---
title: "3x Booting and Trying to Restore Grub"
date: 2009-08-30
forum: General Help
---

### Post by jaqrah on 2009-08-30
Here is the situation:

I was dual booting XP SP3 & Ubuntu 8.10.  I had a spare partition so I finally got around to installing Win7 RC 7100.  Grub has been obliterated and I have been trying to follow various methods to restore Grub.

Here is where I stand:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x70de70de

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1530    12289693+   7  HPFS/NTFS
/dev/sda2            1531        9728    65850435    f  W95 Ext'd (LBA)
/dev/sda5            1531        9728    65850403+   7  HPFS/NTFS

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf769c7f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         733     5887791   83  Linux
/dev/sdb2             734        9729    72260370    5  Extended
/dev/sdb5             734         976     1951866   82  Linux swap / Solaris
/dev/sdb6             977        4866    31246393+  83  Linux
/dev/sdb7            4867        9729    39062016    7  HPFS/NTFS
ubuntu@ubuntu:~$ sudo mkdir /media/root
mkdir: cannot create directory `/media/root': File exists
ubuntu@ubuntu:~$ sudo mount /dev/sdb1 /media/root
ubuntu@ubuntu:~$ sudo ls /media/root
bin    dev   initrd.img      lost+found  opt   sbin  tmp  vmlinuz
boot   etc   initrd.img.old  media	 proc  srv   usr  vmlinuz.old
cdrom  home  lib	     mnt	 root  sys   var  windows
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/media/root /dev/sdb1
grub-setup: warn: Attempting to install GRUB to a partition instead of the MBR.  This is a BAD idea.
grub-setup: warn: Embedding is not possible.  GRUB can only be installed in this setup by using blocklists.  However, blocklists are UNRELIABLE and its use is discouraged.
grub-setup: error: Cannot read `/grub/core.img' correctly
```

The first time I did this routine there wasn't a boot flag for Ubuntu.  I used live cd and gparted to add the boot flag for the Ubuntu / partition.  But then I get that warning at the end...what is that all about?  And just out of perverse curiosity, what would happen if I removed the Win boot flag on /dev/sda1?

Any help would be appreciated.

jaq

---

### Post by jaqrah on 2009-08-30
With further exploration, I realized I made a typing error.

```
sudo grub-install --root-directory=/media/root /dev/sdb1
```

should have been

```
sudo grub-install --root-directory=/media/root /dev/sdb
```

It got rid of the warning error and reported grub was installed.  Unfortunately, it still did not repair or install grub.  :confused:

---

### Post by jaqrah on 2009-08-30
Well...at this juncture, it appears re-installing the root partition is the quickest solution.  It took under 10 minutes.  

It straightened out whatever was wrong with Grub and I am triple booting happily!:)

---

