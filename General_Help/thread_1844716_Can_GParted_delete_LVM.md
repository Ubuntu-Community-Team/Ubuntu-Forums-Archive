---
title: "Can GParted delete LVM?"
date: 2011-09-15
forum: General Help
---

### Post by leviathan8 on 2011-09-15
Hello. I've recently installed Fedora 15 on my laptop, and it partitioned the filesystem as an LVM. I don't have any experience with LVM and I feel confused right now. Fedora was nice and all, but it kept freezing when doing minor changes to settings, when suspending, and such. So right now I'm deciding to wipe the Fedora partition, which is LVM as I understand and leave it as unalocated space for installation of another operating system. 

Can anyone inform me if I am able to delete the Fedora partition using the GParted program from a live environment? 

That's all I need to know right now, thanks for help!

Here is my fdisk output:

```
[adam@laptop ~]$ sudo fdisk -l
[sudo] password for adam: 

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d6931

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   542724095   271361024    7  HPFS/NTFS/exFAT
/dev/sda2   *   542724096   543748095      512000   83  Linux
/dev/sda3       543748096   976773119   216512512   8e  Linux LVM

Disk /dev/mapper/vg_laptop-lv_swap: 3959 MB, 3959422976 bytes
255 heads, 63 sectors/track, 481 cylinders, total 7733248 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_laptop-lv_swap doesn't contain a valid partition table

Disk /dev/mapper/vg_laptop-lv_root: 53.7 GB, 53687091200 bytes
255 heads, 63 sectors/track, 6527 cylinders, total 104857600 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_laptop-lv_root doesn't contain a valid partition table

Disk /dev/mapper/vg_laptop-lv_home: 164.0 GB, 164047618048 bytes
255 heads, 63 sectors/track, 19944 cylinders, total 320405504 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/vg_laptop-lv_home doesn't contain a valid partition table

```

Note however that I want to keep the /dev/sda1 partition, which is not LVM.

---

### Post by FormatSeize on 2011-09-15
GParted does not yet support LVM partition manipulation.

---

### Post by leviathan8 on 2011-09-16
Thank you for the reply. Do you know any way of deleting the LVM partition?

Later edit: I took the risk of deleting the Fedora partition using GParted from a live medium, and everything worked perfectly.

---

### Post by lioncub33 on 2012-08-27
This worked for me (from a GParted Live CD)::guitar:
root@PartedMagic:~# lvm vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vg_jem1gb80gbdesktop" using metadata type lvm2
root@PartedMagic:~# lvm vgremove vg_jem1gb80gbdesktop
Do you really want to remove volume group "vg_jem1gb80gbdesktop" containing 3 logical volumes? [y/n]: y
Do you really want to remove active logical volume lv_root? [y/n]: y
  Logical volume "lv_root" successfully removed
Do you really want to remove active logical volume lv_home? [y/n]: y
  Logical volume "lv_home" successfully removed
Do you really want to remove active logical volume lv_swap? [y/n]: y
  Logical volume "lv_swap" successfully removed
  Volume group "vg_jem1gb80gbdesktop" successfully removed
root@PartedMagic:~#

After this, for some reason the LVM still appeard in GParted, but was no longer locked.. so I deleted it :-) Excellent!

---

### Post by philipcammarata on 2012-08-29
You sir, lioncub33 are my hero.

---

### Post by Tommaso on 2013-01-18
> **lioncub33 said:**
> This worked for me (from a GParted Live CD)::guitar:
root@PartedMagic:~# lvm vgscan
  Reading all physical volumes.  This may take a while...
  Found volume group "vg_jem1gb80gbdesktop" using metadata type lvm2
root@PartedMagic:~# lvm vgremove vg_jem1gb80gbdesktop
Do you really want to remove volume group "vg_jem1gb80gbdesktop" containing 3 logical volumes? [y/n]: y
Do you really want to remove active logical volume lv_root? [y/n]: y
  Logical volume "lv_root" successfully removed
Do you really want to remove active logical volume lv_home? [y/n]: y
  Logical volume "lv_home" successfully removed
Do you really want to remove active logical volume lv_swap? [y/n]: y
  Logical volume "lv_swap" successfully removed
  Volume group "vg_jem1gb80gbdesktop" successfully removed
root@PartedMagic:~#

After this, for some reason the LVM still appeard in GParted, but was no longer locked.. so I deleted it :-) Excellent!

Thanks a ton!!

---

