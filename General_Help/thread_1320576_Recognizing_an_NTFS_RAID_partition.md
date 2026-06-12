---
title: "Recognizing an NTFS RAID partition"
date: 2009-11-09
forum: General Help
---

### Post by giyad on 2009-11-09
Hi, I'm a Linux noob here, just installed Ubuntu 9.04 (Jaunty) 64bit for the first time...

I've been running Vista and I have a 2TB RAID-0 that I want Ubuntu to recognize.  I'm using this RAID drive to store all my media and would like to be able to share it on the network when Ubuntu is running as well.  Is this possible since the partition is NTFS?

Currently I can't find it in "Places", however, I can see the Backup drive (which is an external 2TB) and is also formatted in NTFS.  I can see that drive, but not the RAID (so ntfs-3g is definitely working), i find this weird can anyone explain to me why its doing this?  Could it have something to do with the way it was formatted/setup in windows?  I selected GPT isntead of MBR for many reasons, and linux support was supposed to be one of them...

---

### Post by blueridgedog on 2009-11-09
If the RAID array is a Vista software array, then you will not be able to see it with any other OS.  If it is a hardware array, as in created by a dedicated RAID controller, then you should be able to see it, if you have the kernel module (think driver) for the controller.

How was the array created?

---

### Post by giyad on 2009-11-09
> **blueridgedog said:**
> If the RAID array is a Vista software array, then you will not be able to see it with any other OS.  If it is a hardware array, as in created by a dedicated RAID controller, then you should be able to see it, if you have the kernel module (think driver) for the controller.

How was the array created?
Its a hardware controller through my motherboard EVGA nForce 680i SLI (NVIDIA).  Sorry forgot to mention this.

I've been looking for solutions and in the process I've installed dmraid but I don't want to break the raid so I need to make sure the next steps I take are the right ones haha.  Any ideas?

---

### Post by blueridgedog on 2009-11-09
Can you look in the book that came with the motherboard locate the RAID chip that is used?  We can then see if it is Linux compatible.

Also, can you post the output of 

```
sudo fdisk -l 
```

and

```
lspci
```

---

### Post by giyad on 2009-11-09
No problem, here are the results to fdisk -l:

> Disk /dev/sda: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9fe0643

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18242   146521088    7  HPFS/NTFS

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


[B]Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
256 heads, 63 sectors/track, 121126 cylinders
Units = cylinders of 16128 * 512 = 8257536 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      266306  2147483647+  ee  GPT[/B] 

Disk /dev/sdc: 64.0 GB, 64023257088 bytes
255 heads, 63 sectors/track, 7783 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000df395

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1        7460    59922418+  83  Linux
/dev/sdc2            7461        7783     2594497+   5  Extended
/dev/sdc5            7461        7783     2594466   82  Linux swap / Solaris

WARNING: GPT (GUID Partition Table) detected on '/dev/sdd'! The util fdisk doesn't support GPT. Use GNU Parted.


[B]Disk /dev/sdd: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      121602   976762583+  ee  GPT[/B] 

Disk /dev/sde: 2000.3 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xffa2f4e7

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1      243202  1953512448    7  HPFS/NTFS 
Here are the results of lspci:
> 00:00.0 Host bridge: nVidia Corporation C55 Host Bridge (rev a2)
00:00.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a2)
00:00.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:00.7 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.3 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.4 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.5 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:01.6 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.0 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.1 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:02.2 RAM memory: nVidia Corporation C55 Memory Controller (rev a1)
00:03.0 PCI bridge: nVidia Corporation C55 PCI Express bridge (rev a1)
00:09.0 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a1)
00:0a.0 ISA bridge: nVidia Corporation MCP55 LPC Bridge (rev a2)
00:0a.1 SMBus: nVidia Corporation MCP55 SMBus (rev a2)
00:0a.2 RAM memory: nVidia Corporation MCP55 Memory Controller (rev a2)
00:0b.0 USB Controller: nVidia Corporation MCP55 USB Controller (rev a1)
00:0b.1 USB Controller: nVidia Corporation MCP55 USB Controller (rev a2)
00:0d.0 IDE interface: nVidia Corporation MCP55 IDE (rev a1)
[B]00:0e.0 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.1 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)
00:0e.2 RAID bus controller: nVidia Corporation MCP55 SATA Controller (rev a2)[/B]
00:0f.0 PCI bridge: nVidia Corporation MCP55 PCI bridge (rev a2)
00:0f.1 Audio device: nVidia Corporation MCP55 High Definition Audio (rev a2)
00:11.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:12.0 Bridge: nVidia Corporation MCP55 Ethernet (rev a2)
00:16.0 PCI bridge: nVidia Corporation MCP55 PCI Express bridge (rev a2)
01:00.0 VGA compatible controller: nVidia Corporation G71 [GeForce 7950 GT] (rev a1)
02:07.0 FireWire (IEEE 1394): Texas Instruments TSB43AB22/A IEEE-1394a-2000 Controller (PHY/Link)
03:00.0 PCI bridge: Texas Instruments XIO2000(A)/XIO2200(A) PCI Express-to-PCI Bridge (rev 03)
04:00.0 FireWire (IEEE 1394): Texas Instruments TSB82AA2 IEEE-1394b Link Layer Controller (rev 01)
Also, this is the output of using:
```
dmraid -ay
```> RAID set "nvidia_facfcied" already activeIt seems the RAID is active, maybe I just need to mount it but its not being displayed in places?  Also, I'm not sure if the warning displayed by fdisk means anything, but I did parition the RAID drives in GPT instead of MBR.

---

### Post by giyad on 2009-11-09
Sorry, I had made a mistake earlier in my previous post.  I highlighted the external 2TB drive instead of the two separate drives that are set up in RAID via the motherboard.  I've since corrected this.  Again sorry for the confusion.

---

### Post by falconindy on 2009-11-09
Chances are high this is a fakeraid controller. YMMV, but generally these don't work under Ubuntu.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

### Post by giyad on 2009-11-10
> **falconindy said:**
> Chances are high this is a fakeraid controller. YMMV, but generally these don't work under Ubuntu.

[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)
thanks for that wiki, i came across it earlier but I just don't quite know what to make of it, there is so much going on there.  I don't wish to install Windows onto the RAID, I already have windows installed on a separate drive.

What I need to do is mount an already healthy RAID-0 in Ubuntu.  I'm not sure what to do in order to mount it?  As I said, the "dmraid -ay" command returns "RAID set "nvidia_facfcied" already active", so it should work no?

---

### Post by giyad on 2009-11-10
I hope this helps... I installed Mountmanager and when I opened it up it shows me my drives and their filesystem info.  I've uploaded a picture that shows everything.

I don't know if this is going to help, you can see that the RAID is definitely recognized, but it doesn't show up as a single drive...

---

### Post by falconindy on 2009-11-10
> **giyad said:**
> thanks for that wiki, i came across it earlier but I just don't quite know what to make of it, there is so much going on there.  I don't wish to install Windows onto the RAID, I already have windows installed on a separate drive.

What I need to do is mount an already healthy RAID-0 in Ubuntu.  I'm not sure what to do in order to mount it?  As I said, the "dmraid -ay" command returns "RAID set "nvidia_facfcied" already active", so it should work no?
If that's the case, you should have a device under /dev/nvidia_facfcied/ (or possibly just md0). Mount that, read only at first, until you're sure it's functioning okay.

---

### Post by giyad on 2009-11-10
> **falconindy said:**
> If that's the case, you should have a device under /dev/nvidia_facfcied/ (or possibly just md0). Mount that, read only at first, until you're sure it's functioning okay.

well mounting doesn't work for some reason, let me output exactly what I did and what I got.

```
sudo mount /dev/mapper/nvidia_facfcied /media/Z/ -t ntfs-3g -o nls-utf8,umask=0222


NTFS signature is missing.
Failed to mount '/dev/mapper/nvidia_facfcied': Invalid argument
The device '/dev/mapper/nvidia_facfcied' doesn't seem to have a valid NTFS.
Maybe the wrong device is used? Or the whole disk instead of a
partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

```I should let you know that I created /media/Z as the mount point, so I'm not defining an imaginary mount point up there.

Also, using md0 did not work it just said

```
sudo mount /dev/md0 /media/Z/ -t ntfs -o nls-utf8,umask=0222


ntfs-3g: Failed to access volume '/dev/md0': No such file or directory
Please type '/sbin/mount.ntfs --help' for more information.

```I'm really stumped here...any ideas?

---

### Post by blueridgedog on 2009-11-10
Disregard...obsolete as I did not see the last msg.

---

### Post by giyad on 2009-11-11
heres some more info that may be helpful... I don't see the RAID in the output of $ cat /etc/mtab

> /dev/sdc1 / ext3 rw,relatime,errors=remount-ro 0 0
tmpfs /lib/init/rw tmpfs rw,nosuid,mode=0755 0 0
proc /proc proc rw,noexec,nosuid,nodev 0 0
sysfs /sys sysfs rw,noexec,nosuid,nodev 0 0
varrun /var/run tmpfs rw,nosuid,mode=0755 0 0
varlock /var/lock tmpfs rw,noexec,nosuid,nodev,mode=1777 0 0
udev /dev tmpfs rw,mode=0755 0 0
tmpfs /dev/shm tmpfs rw,nosuid,nodev 0 0
devpts /dev/pts devpts rw,noexec,nosuid,gid=5,mode=620 0 0
fusectl /sys/fs/fuse/connections fusectl rw 0 0
lrm /lib/modules/2.6.28-16-generic/volatile tmpfs rw,mode=755 0 0
securityfs /sys/kernel/security securityfs rw 0 0
binfmt_misc /proc/sys/fs/binfmt_misc binfmt_misc rw,noexec,nosuid,nodev 0 0
gvfs-fuse-daemon /home/ziyad/.gvfs fuse.gvfs-fuse-daemon rw,nosuid,nodev,user=ziyad 0 0
/dev/sde1 /media/Backup fuseblk rw,nosuid,nodev,allow_other,blksize=4096 0 0


---

### Post by giyad on 2009-11-11
bump

---

### Post by giyad on 2009-11-12
Ok, I haven't been getting much help on this issue, but I'm about to try something and I'm hoping someone can tell me whether or not this is a good idea?

What I'm about to do is edit the fstab
```
sudo gedit /etc/fstab
```
I'm going to add the lines
$ /dev/sdb1 /media/Z
$ /dev/sdd1 /media/Z

those are the two partitions that make up my RAID and I guess if I point them to the same mount point, that should work?

---

### Post by giyad on 2009-11-13
bump

---

### Post by giyad on 2009-11-16
Thanks for all your helps guys...
[URL="http://www.linuxquestions.org/questions/linux-hardware-18/mounting-an-ntfs-raid-0-stripe-in-ubuntu-9.04-64-bit-769017/page2.html"]I got it to mount!
[/URL] 
Kudos to mostlyharmless from the linuxquestions.org forums
[URL="http://www.linuxquestions.org/questions/linux-hardware-18/mounting-an-ntfs-raid-0-stripe-in-ubuntu-9.04-64-bit-769017/page2.html"]
[/URL]

---

