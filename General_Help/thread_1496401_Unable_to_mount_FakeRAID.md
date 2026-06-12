---
title: "Unable to mount FakeRAID"
date: 2010-05-29
forum: General Help
---

### Post by anders4431 on 2010-05-29
Hi 

I am unable to mount my fakeRAID, raid 0 array in ubuntu 10.04.

My motherboard is a Gigabyte GA-MA74GM-S2H with BIOS version F4b.

> 
anders@anders-desktop:~$ uname -a
Linux anders-desktop 2.6.32-22-generic #33-Ubuntu SMP Wed Apr 28 13:27:30 UTC 2010 i686 GNU/Linux


anders@anders-desktop:~$ sudo dmraid -s
/dev/sdc: "pdc" and "nvidia" formats discovered (using nvidia)!
/dev/sdc: "sil" and "nvidia" formats discovered (using nvidia)!
*** Active Set
name   : nvidia_fbhfddba
size   : 3907050240
stride : 128
type   : stripe
status : ok
subsets: 0
devs   : 2
spares : 0


anders@anders-desktop:~$ sudo dmraid -r
/dev/sdc: "pdc" and "nvidia" formats discovered (using nvidia)!
/dev/sdc: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdc: nvidia, "nvidia_fbhfddba", stripe, ok, 1953525166 sectors, data@ 0
/dev/sda: nvidia, "nvidia_fbhfddba", stripe, ok, 1953525166 sectors, data@ 0


anders@anders-desktop:~$ sudo dmraid -ay -v
/dev/sdc: "pdc" and "nvidia" formats discovered (using nvidia)!
/dev/sdc: "sil" and "nvidia" formats discovered (using nvidia)!
RAID set "nvidia_fbhfddba" already active
INFO: Activating stripe raid set "nvidia_fbhfddba"
RAID set "nvidia_fbhfddba1" already active
INFO: Activating partition raid set "nvidia_fbhfddba1"
RAID set "nvidia_fbhfddba2" already active
INFO: Activating partition raid set "nvidia_fbhfddba2"
RAID set "nvidia_fbhfddba5" already active
INFO: Activating partition raid set "nvidia_fbhfddba5"
RAID set "nvidia_fbhfddba6" already active
INFO: Activating partition raid set "nvidia_fbhfddba6"


anders@anders-desktop:~$ ls -l /dev/mapper
total 0
crw-rw---- 1 root root  10, 59 2010-05-29 12:53 control
brw-rw---- 1 root disk 252,  0 2010-05-29 12:53 nvidia_fbhfddba
brw-rw---- 1 root disk 252,  1 2010-05-29 12:53 nvidia_fbhfddba1
brw-rw---- 1 root disk 252,  3 2010-05-29 12:53 nvidia_fbhfddba2
brw-rw---- 1 root disk 252,  4 2010-05-29 12:53 nvidia_fbhfddba5
brw-rw---- 1 root disk 252,  5 2010-05-29 12:53 nvidia_fbhfddba6


anders@anders-desktop:~$ sudo fdisk /dev/mapper/nvidia_fbhfddba
WARNING: DOS-compatible mode is deprecated. It's strongly recommended to
         switch off the mode (command 'c') and change display units to
         sectors (command 'u').

Command (m for help): p

Disk /dev/mapper/nvidia_fbhfddba: 2000.4 GB, 2000409722880 bytes
255 heads, 63 sectors/track, 243202 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 65536 bytes / 131072 bytes
Disk identifier: 0xaf909fb9

                      Device Boot      Start         End      Blocks   Id  System
/dev/mapper/nvidia_fbhfddba1               1       12749   102400000   83  Linux
/dev/mapper/nvidia_fbhfddba2           12749      236829  1799921664    7  HPFS/NTFS
/dev/mapper/nvidia_fbhfddba3          236829      243203    51202305    5  Extended
Partition 3 does not start on physical sector boundary.
/dev/mapper/nvidia_fbhfddba5          236829      242937    49062400   83  Linux
/dev/mapper/nvidia_fbhfddba6          242937      243203     2139776   82  Linux swap / Solaris

Command (m for help): q


anders@anders-desktop:~$ sudo mount /dev/mapper/nvidia_fbhfddba2 /mnt -t ntfs
NTFS signature is missing.
Failed to mount '/dev/mapper/nvidia_fbhfddba2': Invalid argument
The device '/dev/mapper/nvidia_fbhfddba2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
[[IMG]http://img29.imageshack.us/img29/8742/screenshot18tbharddiskd.png[/IMG]]("http://img29.imageshack.us/i/screenshot18tbharddiskd.png/")

It's the two 1 TB samsung hard drives that is in the raid 0 array.

Why am i unable to mount the 1.8 TB ntfs partition?

---

### Post by anders4431 on 2010-06-02
It seems like the array is fully detected (sudo fdisk /dev/mapper/nvidia_fbhfddba shows all the partitions on the array).
I am just unable to mount them.

---

