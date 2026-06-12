---
title: "confused chrooter in waiting looking to  grub install from liveDVD"
date: 2012-04-15
forum: General Help
---

### Post by javaholic on 2012-04-15
I'm eventually looking to repair my grub using a liveDVD.  I'm really confused with my partitions when it comes to attempting to chroot the system first.

when i > sudo fdisk -l I get the following:

```
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000537dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    98060759    49030348+  82  Linux swap / Solaris
/dev/sda2        98060760  1953520064   927729652+   5  Extended
/dev/sda5        98060823  1953520064   927729621   83  Linux

Disk /dev/mapper/nvidia_cbddiijb: 1000.2 GB, 1000204884992 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525166 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000537dc

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_cbddiijb1   *          63    98060759    49030348+  82  Linux swap / Solaris
/dev/mapper/nvidia_cbddiijb2        98060760  1953520064   927729652+   5  Extended
/dev/mapper/nvidia_cbddiijb5        98060823  1953520064   927729621   83  Linux

Disk /dev/mapper/nvidia_cbddiijb2: 950.0 GB, 949995164160 bytes
255 heads, 63 sectors/track, 115497 cylinders, total 1855459305 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

                        Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_cbddiijb2p1              63  1855459304   927729621   83  Linux

Disk /dev/mapper/nvidia_cbddiijb5: 950.0 GB, 949995131904 bytes
255 heads, 63 sectors/track, 115496 cylinders, total 1855459242 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/nvidia_cbddiijb5 doesn't contain a valid partition table

Disk /dev/mapper/nvidia_cbddiijb1: 50.2 GB, 50207076864 bytes
255 heads, 63 sectors/track, 6103 cylinders, total 98060697 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/nvidia_cbddiijb1 doesn't contain a valid partition table

```

I took this to mean that i could try either:

```
mount /dev/sda5 /mnt/
```

or ```
mount /dev/mapper/nvidia_cbddiijb5
```

but whenever i try either i get

```
mount: special device /dev/nvidia_cbddiijb5 does not exist
```

Could someone please try and explain what is going on here and what i'm doing wrong

---

### Post by oldfred on 2012-04-15
Are you running RAID or LVM? The mapper is only showing sdb not sda. I do not know RAID so I cannot really help on that.

But with gpt and booting with BIOS (not UEFI) you need a small 1MB bios_grub partition to get grub to correctly install. It can be anywhere on drive.

If using gpt with BIOS create a 1MB bios_grub partition with no format. I used gparted and selected gpt under device, advanced & select gpt over msdos(MBR) default partitioning.... But if you are using RAID you cannot use gparted but have to use whatever mdadm?

All the normal reinstall or chroot instructions I have are for standard partitions, you have to translate to use the RAID/mapper partitions.

Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)
Grub2 info & full chroot version - also see METHOD 3 - CHROOT:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

---

