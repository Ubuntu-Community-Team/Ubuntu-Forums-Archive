---
title: "fdisk command?"
date: 2010-04-30
forum: General Help
---

### Post by spiky001 on 2010-04-30
Is there a command that tells you what the partitions are 
fdisk -l shows partitions  I want to know which is root swap home etc, Labels the partitions?

---

### Post by mikewhatever on 2010-04-30
df -h

and fdisk labels swap as 'Linux swap'.

---

### Post by spiky001 on 2010-04-30
Thks

---

### Post by ajgreeny on 2010-04-30
Gparted or the command line tune2fs can both label partitions to what you want them to be.  I find tune2fs quickest and most useful.

For example ```
sudo tune2fs -L Lucid /dev/sdb2
```will label sdb2 as Lucid as shown in sudo blkid output
```
/dev/sda1: LABEL="Ubuntu910" UUID="b5b360fe-f23d-4fc3-81f4-2e2b77c0b103" TYPE="ext4" 
/dev/sda2: LABEL="UbuntuHome" UUID="e2554df2-7e16-4864-97c9-834d8bebecda" TYPE="ext4" 
/dev/sda5: UUID="1bfd912d-b6b6-4a68-9aaf-4139513772ec" TYPE="swap" 
/dev/sdb1: LABEL="Karmic" UUID="499975f7-bef1-4de5-9b9d-da96c1bd6c9f" TYPE="ext4" 
/dev/sdb2: LABEL="Lucid" UUID="33c16558-79a8-4574-9b9b-d4bd66112aa3" TYPE="ext4" 
/dev/sdb3: LABEL="Mint8" UUID="1cf34e83-4b6f-40b6-b2d1-5e0d35c95f7d" TYPE="ext4"
```
As you can see I have been trying a lot of different versions of ubuntu, and need to have a bit of a sortout of disks/partitions, but I tend to try things on test partitions before going full tilt into a distro version..

---

### Post by srs5694 on 2010-04-30
FWIW, if you switch from the Master Boot Record (MBR) partition system to the GUID Partition Table (GPT) system, you'll gain a partition name field in every partition definition, which you can use to identify what a partition is for. For instance, here's one of the disks on one of my computers:

```

# gdisk -l /dev/hdb
GPT fdisk (gdisk) version 0.6.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/hdb: 312581808 sectors, 149.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2C158E64-5AA9-1E5E-72E6-13107493F01E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Partitions will be aligned on 1-sector boundaries
Total free space is 5351 sectors (2.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63          401624   196.1 MiB   0700  Ubuntu /boot
   5          401688          803249   196.1 MiB   0700  Debian /boot
   6          803313         1204874   196.1 MiB   EF00  Fedora 12 32-bit /boot
   7         1204938       274663304   130.4 GiB   8E00  LVM (Halrloprillalar 2)
   8       274663368       312576704   18.1 GiB    0700  Shared (FAT-32)

```

Note the three early ~200MiB partitions are separate /boot partitions for three OS installations (Ubuntu, Debian, and Fedora), the disk has a Logical Volume Management (LVM) partition and a shared FAT-32 partition. This feature can really help disambiguate systems that have lots of partitions of a particular type. Unfortunately, GParted doesn't provide access to this information, although the text-mode GNU Parted does. Go figure.

---

### Post by sysabod on 2010-04-30
> **srs5694 said:**
> FWIW, if you switch from the Master Boot Record (MBR) partition system to the GUID Partition Table (GPT) system, you'll gain a partition name field in every partition definition, which you can use to identify what a partition is for. For instance, here's one of the disks on one of my computers:

```

# gdisk -l /dev/hdb
GPT fdisk (gdisk) version 0.6.6

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/hdb: 312581808 sectors, 149.1 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 2C158E64-5AA9-1E5E-72E6-13107493F01E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 312581774
Partitions will be aligned on 1-sector boundaries
Total free space is 5351 sectors (2.6 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              63          401624   196.1 MiB   0700  Ubuntu /boot
   5          401688          803249   196.1 MiB   0700  Debian /boot
   6          803313         1204874   196.1 MiB   EF00  Fedora 12 32-bit /boot
   7         1204938       274663304   130.4 GiB   8E00  LVM (Halrloprillalar 2)
   8       274663368       312576704   18.1 GiB    0700  Shared (FAT-32)

```Note the three early ~200MiB partitions are separate /boot partitions for three OS installations (Ubuntu, Debian, and Fedora), the disk has a Logical Volume Management (LVM) partition and a shared FAT-32 partition. This feature can really help disambiguate systems that have lots of partitions of a particular type. Unfortunately, GParted doesn't provide access to this information, although the text-mode GNU Parted does. Go figure.
it seems my system does not support this 'gdisk ' command,
my ubuntu 9.10 complains command not found.

---

### Post by srs5694 on 2010-04-30
> **sysabod said:**
> it seems my system does not support this 'gdisk ' command,
my ubuntu 9.10 complains command not found.

You can download it from its [Sourceforge page.](http://sourceforge.net/projects/gptfdisk/files/) (Get the .deb file for your distribution and install it.) I believe it's been added to 10.04, but that version is already a bit out of date. As noted in my original post, you can also see GPT partition names via the GNU Parted utility (command name parted), as in "sudo parted /dev/sda print".

Note that gdisk is only useful if you've already got at least one GPT disk, plan to (re)-partition a disk as GPT, or plan to convert an MBR disk to GPT. It won't add volume names to an MBR disk except by converting it to GPT format.

---

