---
title: "Rescuing an LUKS-encrypted LVM volume"
date: 2012-04-27
forum: General Help
---

### Post by andthen.. on 2012-04-27
Quite a while back I installed xubuntu 11.10 on an LUKS-encrypted LVM setup from the directions from this web page:
[www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/]("http://www.linuxbsdos.com/2011/05/10/how-to-install-ubuntu-11-04-on-an-encrypted-lvm-file-system/") 

Then recently I wanted to make the volume group bigger giving me more free space on my logical volumes.

Soo.. I read somewhere that to do this you can create another physical volume (another partition) and then include this physical volume in the volume group. I encrypted this partition before I added it. Then when I added it to the volume group, it registered as full! So I couldn't expand the existing logical volumes and was left with next to NO free space :confused:

RESULTS:
So I ended up in a pickle with even less free space than before.  So I just deleted the physical volume I had created using gparted. Which I now regret because I cant access the original logical volumes at all now! :(

I did reinstall an operating system on the remaining disk space though so I could begin trying to recover my data.

When I did this I was away travelling and I had limited disk storage. Now I am back I have all the disk space I need.

So, before I began investigating I backed-up my two physical volumes as disk images into two files:
sda2.img
sdb2.img
by running:
```

sudo dd if=/dev/sda2 of=/media/external_drive/sda2.img
sudo dd if=/dev/sdb2 of=/media/external_drive/sdb2.img

```
My first question is: Is this method a reliable backup of my data?
My second question is: How do I get my original data back?

Please help!

######################################################################################

INFORMATION:
```

bob@xu:~$ sudo pvscan

  PV /dev/sda2   VG vg-eeepc   lvm2 [7.27 GiB / 7.27 GiB free]    #inaccessible encrypted partition
  PV /dev/sdb2   VG vg-eeepc   lvm2 [9.88 GiB / 9.88 GiB free]    #inaccessible encrypted partition
  PV /dev/dm-0   VG system     lvm2 [19.84 GiB / 0    free]            #current working operating system
  Total: 3 [36.98 GiB] / in use: 3 [36.98 GiB] / in no VG: 0 [0   ]

bob@xu:~$ sudo vgscan

  Found volume group "vg-eeepc" using metadata type lvm2    #old volume group I want access to
  Found volume group "system" using metadata type lvm2       #new volume group with operating system on

bob@xu:~$ sudo lvscan

  ACTIVE            '/dev/system/swap' [380.00 MiB] inherit    #my old logical volumes are nowhere to be seen :-(
  ACTIVE            '/dev/system/rooot' [19.46 GiB] inherit

bob@xu:~$ sudo blkid

/dev/sda1: UUID="6e88fefe-c076-434a-a755-b2f074fb46c9" TYPE="crypto_LUKS" 
/dev/sda2: UUID="Z7Eo81-RL0w-r2s9-Q71f-jaqP-zUOM-Uzn2UA" TYPE="LVM2_member" 
/dev/sdb1: UUID="8c80b9f2-4ee7-4fbe-abdc-397719409bb1" TYPE="crypto_LUKS" 
/dev/sdb2: UUID="0spgbA-M3Zy-H95e-23aa-TImg-AhaM-9oQbkm" TYPE="LVM2_member" 
/dev/mapper/sdb1_crypt: UUID="Yq1JyT-2wH0-qioT-WTCu-i3Vv-Ppn0-G8M16I" TYPE="LVM2_member" 
/dev/mapper/system-swap: UUID="f9ea8403-9ae8-4e10-acc3-5915e0879ff5" TYPE="swap" 
/dev/mapper/system-rooot: UUID="926c50b9-3a2b-402e-a146-937c712496a7" TYPE="ext4" 

bob@xu:~$ sudo fdisk -l

Disk /dev/sda: 8061 MB, 8061419520 bytes
255 heads, 63 sectors/track, 980 cylinders, total 15744960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009d964

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      503807      250880   83  Linux
/dev/sda2          503808    15742975     7619584   8e  Linux LVM

Disk /dev/sdb: 31.9 GB, 31914983424 bytes
255 heads, 63 sectors/track, 3880 cylinders, total 62333952 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ee397

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048    41609215    20803584   83  Linux
/dev/sdb2        41609216    62332927    10361856   8e  Linux LVM

Disk /dev/mapper/sdb1_crypt: 21.3 GB, 21301817344 bytes
255 heads, 63 sectors/track, 2589 cylinders, total 41605112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sdb1_crypt doesn't contain a valid partition table

Disk /dev/mapper/system-swap: 398 MB, 398458880 bytes
255 heads, 63 sectors/track, 48 cylinders, total 778240 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/system-swap doesn't contain a valid partition table

Disk /dev/mapper/system-rooot: 20.9 GB, 20900216832 bytes
255 heads, 63 sectors/track, 2540 cylinders, total 40820736 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/system-rooot doesn't contain a valid partition table

```######################################################################################

IDEA 1:
Should I edit /etc/crypttab or /etc/fstab?

```

bob@xu:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# /boot was on /dev/sda1 during installation
UUID=6e88fefe-c076-434a-a755-b2f074fb46c9 /boot           ext2    defaults        0       2
/dev/mapper/system-rooot /               ext4    errors=remount-ro 0       1
/dev/mapper/system-swap none            swap    sw              0       0

bob@xu:~$ cat /etc/crypttab 
sdb1_crypt UUID=8c80b9f2-4ee7-4fbe-abdc-397719409bb1 none luks
sda2_crypt UUID=Z7Eo81-RL0w-r2s9-Q71f-jaqP-zUOM-Uzn2UA none luks
sdb2_crypt UUID=0spgbA-M3Zy-H95e-23aa-TImg-AhaM-9oQbkm none luks
 
```+ Oh ye & Im running Xubuntu 11.10

######################################################################################

HALF AN IDEA:
Most help I have come across on the net recommend I run:

```
sudo cryptsetup luksOpen /dev/sda2 encrypted_partition
sudo cryptsetup luksOpen /dev/sdb2 encrypted_partition
```However, they both come up with:

```
"Device /dev/sda2 is not a valid LUKS device."
"Device /dev/sdb2 is not a valid LUKS device."
```(such as [www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html]("http://www.ubuntugeek.com/rescue-an-encrypted-luks-lvm-volume.html"))

######################################################################################

Please help! :)

---

