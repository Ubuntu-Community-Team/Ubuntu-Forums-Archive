---
title: "Mounting an ACOMDATA external hard drive"
date: 2010-01-02
forum: General Help
---

### Post by aust77 on 2010-01-02
Hello,

I'm using Ubuntu 9.04, and I can't seem to get my ACOMDATA external hard drive to work. It is plugged into the PC using a USB cable, and it is read as a removable storage device on both Win. XP and Win. 7. On Ubuntu, it is read for a split-second, then disappears. All of my USB ports are functioning perfectly. Are there any commands to mount this device? Thanks,




aust77

---

### Post by Leppie on 2010-01-02
does the disk show under "sudo fdisk -l"?

---

### Post by aust77 on 2010-01-02
I thank you for your speedy response, and apologise for my delayed response. I figured sudo fdisk -l was the command to run. An "extended" drive was reported in /dev/sda2, but I had a personal USB device inside one of my slots, so that could be it. After unplugging it, this was the results:
Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d052d04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9686    77802763+  83  Linux
/dev/sda2            9687        9964     2233035    5  Extended
/dev/sda5            9687        9964     2233003+  82  Linux swap / Solaris

Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab957d34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       11729    94208000    7  HPFS/NTFS
/dev/sdc2           11729       14947    25848832    7  HPFS/NTFS

Since my USB mass storage device was removed, it must be the extended /dev/sda2 one or one of the /dev/sdcs. Even if I am right, I am not sure of the command to run to mount it, nor what to google search. Thanks for your time,



aust77

---

### Post by Rodemire on 2010-01-02
> **Leppie said:**
> does the disk show under "sudo fdisk -l"?

Hi, 

Sorry aust77 for riding on your thread but i have a similar problem. Sometimes when i switch on my Toshiba external hard drive it gets picked up and at other times it doesnt. I use Karmic. When it wasn't picked up, I tried the command "lsusb" to see if it was there and it was, this is the output:

Bus 001 Device 003: ID 19d2:0063 ONDA Communication S.p.A. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 004: ID 0930:0b09 Toshiba Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 002: ID 046d:c517 Logitech, Inc. LX710 Cordless Desktop Laser
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

------------------------------------------------------------------------------------

Than i tried fdisk -l as above and did not pick it up, the output is:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xb678b678

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sda2            2551       60801   467901157+   f  W95 Ext'd (LBA)
/dev/sda5            2551       30979   228355911    7  HPFS/NTFS
/dev/sda6           30980       60801   239545183+  83  Linux

Disk /dev/sdb: 20.0 GB, 20020396032 bytes
255 heads, 63 sectors/track, 2434 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xa375a375

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2327    18691596   83  Linux
/dev/sdb2            2328        2434      859477+   5  Extended
/dev/sdb5            2328        2434      859446   82  Linux swap / Solaris
-----------------------------------------------------------------------------------------------

In my setup I have two internal harddrives (sda and sdb) one being 500Gb and the other 20Gb. 

Why does my external harddrive not get picked up and how can i mount it?

---

### Post by scouser73 on 2010-01-02
> **aust77 said:**
> Hello,

I'm using Ubuntu 9.04, and I can't seem to get my ACOMDATA external hard drive to work. It is plugged into the PC using a USB cable, and it is read as a removable storage device on both Win. XP and Win. 7. On Ubuntu, it is read for a split-second, then disappears. All of my USB ports are functioning perfectly. Are there any commands to mount this device? Thanks,




aust77

Please follow the instructions set out in this tutorial for mounting drives: [[COLOR="Red"]**Mount Hard Drives**[/COLOR]]("https://help.ubuntu.com/community/Mount/")

---

### Post by aust77 on 2010-01-02
Thanks scouser, I will read it and tell you the outcome.



aust77

---

### Post by Leppie on 2010-01-02
> **aust77 said:**
> Disk /dev/sdc: 122.9 GB, 122942324736 bytes
255 heads, 63 sectors/track, 14946 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xab957d34

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       11729    94208000    7  HPFS/NTFS
/dev/sdc2           11729       14947    25848832    7  HPFS/NTFS

Since my USB mass storage device was removed, it must be the extended /dev/sda2 one or one of the /dev/sdcs. Even if I am right, I am not sure of the command to run to mount it, nor what to google search. Thanks for your time,
/dev/sda is the first harddrive. partitions on a drive are numbered, so the first partition on the first drive is /dev/sda1. knowing this, sda2 cannot be a standalone disk.

to mount partitions, you need the mount command and a mount point. for example:
```
$sudo mkdir /mnt/test  ##create the mount point
$sudo mount -t ntfs -r /dev/sdc1 /mnt/test  ##mount the first partition of disk sdc as read only for the moment
```

---

### Post by Leppie on 2010-01-02
> **Rodemire said:**
> Sorry aust77 for riding on your thread but i have a similar problem.
hi, did you start a thread for this?
i think it actually maybe something like cables, etc.

---

### Post by aust77 on 2010-01-02
I read the guide posted, and I hate to say this, but ACOMDATA is difficult to get onto Ubuntu. I ran various commands, trying to mount /dev/sdc1, sdc2, sda2, but they all returned this message:
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?


When running the "lsusb" command, I can see my device listed as no.1:
Bus 001 Device 006: ID 0c0b:b157 Dura Micro, Inc. (Acomdata) 
Bus 001 Device 004: ID 05dc:a701 Lexar Media, Inc. JumpDrive FireFly
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 046d:0a01 Logitech, Inc. USB Headset
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 045e:0053 Microsoft Corp. Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


Thank you very much for your extended assistance,



aust77

---

### Post by Leppie on 2010-01-02
> **aust77 said:**
> I read the guide posted, and I hate to say this, but ACOMDATA is difficult to get onto Ubuntu. I ran various commands, trying to mount /dev/sdc1, sdc2, sda2, but they all returned this message:
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
could you post the command you used to mount sdc1?

and as per your post, sda2 is the extended partition (it only is a container for sda5):
> **aust77 said:**
> Disk /dev/sda: 81.9 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2d052d04

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9686    77802763+  83  Linux
**/dev/sda2            9687        9964     2233035    5  Extended**
/dev/sda5            9687        9964     2233003+  82  Linux swap / Solaris


What is the actual size of the ACOMDATA drive?

---

### Post by aust77 on 2010-01-02
The ACOMDATA drive is 120GB.

Here is what I issued for mount sdc1 (I probably went wrong, but I'm a total partition noob :( )
sudo mount -t ntfs -r /dev/sdc1 /mnt/sdc1


I cannot thank you enough.



aust77

---

### Post by Leppie on 2010-01-02
> **aust77 said:**
> The ACOMDATA drive is 120GB.
so most probably this is sdc (as it is around 120gb reading the fdisk info you provided) ;)

> **aust77 said:**
> Here is what I issued for mount sdc1 (I probably went wrong, but I'm a total partition noob :( )
sudo mount -t ntfs -r /dev/sdc1 /mnt/sdc1
did you ceate the mountpoint first? the folder /mnt does exist, but you have to create all mountpoints before being able to use them (except for the ones handled by the system):
```
$sudo mkdir /mnt/sdc1
```

---

### Post by aust77 on 2010-01-02
I worked previously with a Windows NAS, so I know about creating mountpoints. The first thing I did was make /mnt/sdc1.

Unfortunately, a program called ntfs-3g is "invading" my mount attempts, giving me this:
ntfs-3g: Failed to access volume '/dev/sdc1': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

Any way to stop this program from "interfering"? Thanks,



aust77

---

### Post by aust77 on 2010-01-02
I tried a separated command, with bad results:

[B]sudo ntfs-3g /dev/sdc1 /mnt/sdc1
NTFS signature is missing.
Failed to mount '/dev/sdc1': Invalid argument
The device '/dev/sdc1' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?
[/B]

---

### Post by Leppie on 2010-01-02
is this a basic ntfs volume? or was this disk converted to dynamic volume?

---

### Post by aust77 on 2010-01-02
Basic

---

### Post by Leppie on 2010-01-02
then could it be this disk is formatted to hpfs and not ntfs?

---

### Post by Rodemire on 2010-01-03
> **Leppie said:**
> hi, did you start a thread for this?
i think it actually maybe something like cables, etc.

Ni i hadn't started a thread yet. I thought I could get help here. If it may be of assistance, when i plugged in my hard drive, i typed dmesg and the last couple of lines were as follows:

[ 1008.377727] usb 1-6: USB disconnect, address 2
[ 1051.652060] usb 1-6: new high speed USB device using ehci_hcd and address 3
[ 1051.804489] usb 1-6: configuration #1 chosen from 1 choice
[ 1051.813956] usb_storage: `' invalid for parameter `delay_use'

---------------------------------------------------------------------------------------------------

I think that could be the problem but i do not know what to do from now.

---

### Post by Leppie on 2010-01-05
I found an old thread, seems like they build in some stuff that allows mounting only under windows or mac os.
see this post for instructions: [http://ubuntuforums.org/showpost.php?p=3013531&postcount=6](http://ubuntuforums.org/showpost.php?p=3013531&postcount=6)

---

### Post by aust77 on 2010-01-08
Sorry for my long time away, it was family matters. I literally have no clue as to what HPFS is, so what are you suggesting? Do I mount using the mount command with -t hpfs?

---

### Post by Leppie on 2010-01-08
did you have a look at this link: [http://ubuntuforums.org/showpost.php?p=3013531&postcount=6](http://ubuntuforums.org/showpost.php?p=3013531&postcount=6)

---

### Post by aust77 on 2010-01-08
Yes, and I copied the .dll from my Win.XP box. Unfortunately, when running a specified command, these results were returned:
wine ONSPCLCK.exe
wine: could not load L"C:\\windows\\system32\\ONSPCLCK.exe": Module not found

---

### Post by Leppie on 2010-01-08
i found a tool to flash the eeprom of the housing.
if you want i can send you the link, though flashing it may void your warranty.

---

### Post by aust77 on 2010-02-07
Alas, after so much work and tons of help from Leppie, I finally took the whole thing apart and just reformatted it to exFAT. I know it doesn't work with Ubuntu just yet (exFAT) but it's better on Windows PCs than a corrupt NTFS format. Many thanks,

aust77

---

