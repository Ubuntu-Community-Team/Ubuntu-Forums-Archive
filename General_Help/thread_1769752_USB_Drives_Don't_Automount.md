---
title: "USB Drives Don't Automount"
date: 2011-05-28
forum: General Help
---

### Post by Wbie on 2011-05-28
I've got a fresh and clean install of 11.04 and everything is running smoothly save for my USB drives.  The drives are plugged in but not accessible (or viewable) when I go into Computer.

Here's what I see in Terminal:

@Desktop:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 006: ID 03f0:3207 Hewlett-Packard 
Bus 001 Device 005: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
- - - - - 

It seems like the devices are recognized on some level but not in the GUI.  The Hewlett-Packard device is my USB drive.  The Genesys Logic, INC are 4 port hubs I had to install because I only have two hardwired.

Any help would be much appreciated.  My computer is very unusable when not able to access these devices.

---

### Post by JustinMoco on 2011-05-28
I have the same problem On one computer they automount fine .. (an old HP running 11.04) 

On the computer I built yesterday with an ASrock Motherboard I can see the drive int the disk utility .. and when I try to mount it is says it's already mounted .. 

I wonder if it's possible that it's a bios settings issue ?

---

### Post by coffeecat on 2011-05-28
@Wbie and @JustinMoco, have you installed the application "usbmount". If you have, uninstall it and your problems will go.

If not, attach and switch on the USB drive, then run this from a terminal and post the output:

```
dmesg | tail
```

---

### Post by JustinMoco on 2011-05-28
Usbmount was not installed .. 

here is the output ..  The Hard disk is "FAT32" (for reasons of compatibility) ..

justin@justin-luggable:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 003: ID 046d:c062 Logitech, Inc. 
Bus 004 Device 002: ID 0dc6:3401 Precision Squared Technology Corp. 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
justin@justin-luggable:~$ dmesg|tail
[  354.524115] sd 4:0:0:0: [sdb] Mode Sense: 2f 08 00 00
[  354.525906] sd 4:0:0:0: [sdb] No Caching mode page present
[  354.525922] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  354.529899] sd 4:0:0:0: [sdb] No Caching mode page present
[  354.529919] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  354.574180]  sdb: sdb1
[  354.577524] sd 4:0:0:0: [sdb] No Caching mode page present
[  354.577539] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[  354.577552] sd 4:0:0:0: [sdb] Attached SCSI disk
[  355.105840] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
justin@justin-luggable:~$ 

For comparison .. (this is the other machine where it mounts fine)

justin@PMCDesk:~$ lsusb
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0bc2:2300 Seagate RSS LLC 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
justin@PMCDesk:~$ dmesg|tail
[161889.525789] sd 5:0:0:0: [sdb] Write Protect is off
[161889.525798] sd 5:0:0:0: [sdb] Mode Sense: 2f 08 00 00
[161889.529797] sd 5:0:0:0: [sdb] No Caching mode page present
[161889.529810] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[161889.532988] sd 5:0:0:0: [sdb] No Caching mode page present
[161889.533005] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[161889.578569]  sdb: sdb1
[161889.582711] sd 5:0:0:0: [sdb] No Caching mode page present
[161889.582726] sd 5:0:0:0: [sdb] Assuming drive cache: write through
[161889.582737] sd 5:0:0:0: [sdb] Attached SCSI disk
justin@PMCDesk:~$

---

### Post by Wbie on 2011-05-28
> **coffeecat said:**
> @Wbie and @JustinMoco, have you installed the application "usbmount". If you have, uninstall it and your problems will go.

If not, attach and switch on the USB drive, then run this from a terminal and post the output:

```
dmesg | tail
```

Thanks CoffeeCat

No usbmount.

@Desktop:~$ dmesg | tail
[   16.469304] agpgart-via 0000:00:00.0: bridge is in legacy mode, falling back to 2.x
[   16.469316] agpgart-via 0000:00:00.0: putting AGP V2 device into 4x mode
[   16.469378] pci 0000:01:00.0: putting AGP V2 device into 4x mode
[   17.383082] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[   22.128023] eth0: no IPv6 routers present
[   29.504792] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro,commit=0
[  766.032753] vboxdrv: Found 1 processor cores.
[  766.036962] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[  766.036971] vboxdrv: Successfully loaded version 4.0.8 (interface 0x00180000).
[13785.757112] exe (7166): /proc/7166/oom_adj is deprecated, please use /proc/7166/oom_score_adj instead.

---

### Post by coffeecat on 2011-05-28
@JustinMoco, did you notice that in your machine that doesn't mount the USB device, there's an extra line in the output from dmesg? This

```
[  355.105840] EXT4-fs (sdb1): VFS: Can't find ext4 filesystem
```Which is interesting since you say that it's a FAT32 filesystem. I'm puzzled. It would be interesting to run this in both systems with the drive attached:

```
sudo fdisk -lu
```Just to see what the partition table is showing. The output should be the same in both, but let's see.

@Wbie, there does not seem to be any reaction from dmesg when you plug your USB drive in. A couple of questions. Does this HP drive work with another computer and/or operating system? Although lsusb identifies the USB device, the system is apparently not "seeing" the drive itself. What is it, a flash drive or hard drive? It might also be useful to run the same command as I've suggested to JustinMoco. Plug the HP device in, open a terminal and post the output of:

```
sudo fdisk -lu
```Although, tbh, I doubt whether this will show anything associated with the device, but we need to prove this.

---

### Post by JustinMoco on 2011-05-28
output from machine that will mount ..

Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad998

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   315525119   157761536   83  Linux
/dev/sda2       315527166   321671167     3072001    5  Extended
/dev/sda5       315527168   321671167     3072000   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e9858

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    b  W95 FAT32
justin@PMCDesk:~$ 

And the machine that doesn't liek it ..

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

justin@justin-luggable:~$ sudo fdisk -lu
[sudo] password for justin: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000802e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1951444991   975721472   83  Linux
/dev/sda2      1951447038  1953523711     1038337    5  Extended
/dev/sda5      1951447040  1953523711     1038336   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e9858

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    b  W95 FAT32
justin@justin-luggable:~$ 


which looks to my untrained eye to be exactly the same ..

---

### Post by coffeecat on 2011-05-28
> **JustinMoco said:**
> which looks to my untrained eye to be exactly the same ..

Well, my eye is getting weary trying to read that unformatted output. Before we go any further, let me introduce you to [BBCode]("http://ubuntuforums.org/showthread.php?t=1006656"). See what a difference it makes:


> **JustinMoco said:**
> output from machine that will mount ..

```
Disk /dev/sda: 164.7 GB, 164696555520 bytes
255 heads, 63 sectors/track, 20023 cylinders, total 321672960 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ad998

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   315525119   157761536   83  Linux
/dev/sda2       315527166   321671167     3072001    5  Extended
/dev/sda5       315527168   321671167     3072000   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e9858

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    b  W95 FAT32
justin@PMCDesk:~$ 
```And the machine that doesn't liek it ..

```
To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

justin@justin-luggable:~$ sudo fdisk -lu
[sudo] password for justin: 

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000802e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  1951444991   975721472   83  Linux
/dev/sda2      1951447038  1953523711     1038337    5  Extended
/dev/sda5      1951447040  1953523711     1038336   82  Linux swap / Solaris

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000e9858

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63  1953520064   976760001    b  W95 FAT32
justin@justin-luggable:~$ 
```

Anyway, that comment "EXT4-fs (sdb1): VFS: Can't find ext4 filesystem" from the affected machine needs investigating further. You may be right that it's a BIOS issue, but post the output of (with the sdb device plugged in):

```
cat /etc/fstab
sudo blkid
```Wrapping the output in code tags will be useful. :wink:

---

### Post by JustinMoco on 2011-05-28
Does this mean anything ?  

```
justin@justin-luggable:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/sdb1       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c681cf96-9cb3-437d-81d8-25aafcf05c66 none            swap    sw              0       0
justin@justin-luggable:~$ sudo blkid
[sudo] password for justin: 
/dev/sda1: UUID="cee9ef35-4747-4d98-8efc-64f2a12c6f37" TYPE="ext4" 
/dev/sda5: UUID="c681cf96-9cb3-437d-81d8-25aafcf05c66" TYPE="swap" 
justin@justin-luggable:~$ 
```

---

### Post by coffeecat on 2011-05-28
> **JustinMoco said:**
> Does this mean anything ?  

Yes. There had to be a reason for your system trying to find an ext4 filesystem in a partition formatted fat32, and here it is:

```
justin@justin-luggable:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
[COLOR=Red]/dev/sdb1[/COLOR]       /               ext4    errors=remount-ro 0       1
# swap was on /dev/sdb5 during installation
UUID=c681cf96-9cb3-437d-81d8-25aafcf05c66 none            swap    sw              0       0
justin@justin-luggable:~$ sudo blkid
[sudo] password for justin: 
/dev/sda1: UUID="cee9ef35-4747-4d98-8efc-64f2a12c6f37" TYPE="ext4" 
/dev/sda5: UUID="c681cf96-9cb3-437d-81d8-25aafcf05c66" TYPE="swap" 
justin@justin-luggable:~$ 
```My guess is that the /dev/sdb1 line is for your root partition, so how on earth Ubuntu is booting up when it sees your root partition as sda1 is beyond me. Whatever, this is the reason your USB drive, which is sdb, is not being automounted.

A couple of curiosities from this. Did you install your system from the alternate CD? Normally, the installer uses UUIDs to identify partitions in /etc/fstab, but I installed Natty from the alternate CD the other day and the root line in /etc/fstab was similar to yours - no UUID - which surprised me. Also - did you use a live USB rather than CD? This could be why your hard drive was designated sdb instead of sda during install.

The answer is to edit that /etc/fstab line. Do you need any help with this?

---

### Post by JustinMoco on 2011-05-28
Heroic !  .. and I can you how I managed to do it !

The installation was made from a compact flash card, which was on the ATA connector of the motherboard .. (An ide-cf adapter) .. this was then removed after the installation to the first ATA drive .. 

So I changed the SDB1 to SDA1 .. and it all works fine and the USB appears as it should ..

---

