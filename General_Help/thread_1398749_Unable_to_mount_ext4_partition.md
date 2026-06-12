---
title: "Unable to mount ext4 partition"
date: 2010-02-04
forum: General Help
---

### Post by bernardomh on 2010-02-04
Still a novice in Ubuntu (Karmic Koala). I'm trying to mount an ext4 20GB partition of my hard drive so that i can use it to store data, i want it to appear on my desktop as well as on places, as far as i know this is achieved by mounting the partition in /media. At my first attempt i used the following commands. (i named the partition ondskapt)

```

sudo mkdir /ondskapt
sudo gedit /etc/fstab
```
in this document i added the following at the end:
/dev/sda4 /ondskapt ext4 defauts 0 0 
then:

```

sudo mount /ondskapt
df -h /ondskapt
```

when typing the following commands:

```

sudo blkid -c /dev/null
/dev/sda1: LABEL="PQSERVICE" UUID="0159-6699" TYPE="vfat" 
/dev/sda2: UUID="A4A48D83A48D58A6" LABEL="ACER" TYPE="ntfs" 
/dev/sda4: LABEL="Ondskapt" UUID="28ccce8f-b3fa-44ff-90e7-3a092f182117" TYPE="ext4" 
/dev/sda5: UUID="77133c9b-54d1-49b8-a305-a49797a032fb" TYPE="ext4" 
/dev/sda6: UUID="d571c3a0-4a85-4955-ad19-6c67d9755851" TYPE="swap" 
/dev/mmcblk0p1: SEC_TYPE="msdos" UUID="423D-2191" TYPE="vfat" 
/dev/mmcblk1p1: SEC_TYPE="msdos" LABEL="PROYECTO" UUID="6445-F456" TYPE="vfat" 
/dev/sdb1: UUID="32C4647DC46444E7" LABEL="Iomega HDD" TYPE="ntfs" 
/dev/sdc1: LABEL="ONDSKAPT" UUID="44F1-51B4" TYPE="vfat" 
/dev/sdd1: LABEL="IOMEGA_HDD" UUID="317F-1EE2" TYPE="vfat" 


sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x11a8ba38

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         637     5116671   12  Compaq diagnostics
/dev/sda2   *         638        5517    39198600    7  HPFS/NTFS
/dev/sda3            8068       14593    52420095    f  W95 Ext'd (LBA)
/dev/sda4            5518        8067    20482875   83  Linux
/dev/sda5            8068       14321    50235223+  83  Linux
/dev/sda6           14322       14593     2184808+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/mmcblk0: 125 MB, 125960192 bytes
8 heads, 32 sectors/track, 961 cylinders
Units = cylinders of 256 * 512 = 131072 bytes
Disk identifier: 0x00000000

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk0p1               1         961      122959+   6  FAT16

Disk /dev/mmcblk1: 64 MB, 64225280 bytes
4 heads, 32 sectors/track, 980 cylinders
Units = cylinders of 128 * 512 = 65536 bytes
Disk identifier: 0xd084bdc6

        Device Boot      Start         End      Blocks   Id  System
/dev/mmcblk1p1               1         980       62656    6  FAT16
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(1, 0, 1) logical=(0, 1, 1)
Partition 1 has different physical/logical endings:
     phys=(979, 3, 32) logical=(979, 0, 32)

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xcb4a53fb

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       60801   488384001    7  HPFS/NTFS

Disk /dev/sdc: 3965 MB, 3965714432 bytes
128 heads, 63 sectors/track, 960 cylinders
Units = cylinders of 8064 * 512 = 4128768 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               2         960     3866624    b  W95 FAT32

Disk /dev/sdd: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9641a75a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       19457   156288321    b  W95 FAT32

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# / was on /dev/sda5 during installation
UUID=77133c9b-54d1-49b8-a305-a49797a032fb /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=d571c3a0-4a85-4955-ad19-6c67d9755851 none            swap    sw              0       0
#ondskapt
/dev/sda4 ext4 /media/ defaults 0 0



```

I don't know what most of this information means and the "ondskapt" partition does not appear in places or in my desktop. The other ONDSKAPT is a usb memory.
Please help!
Thanx in advance!

---

### Post by djchandler on 2010-02-04
Have you tried using **System>Administration>Disk Utility**? I don't remember if it installs by default or not. If it doesn't, it should.

If not, you can find it in **Ubuntu Software Center** under **System Tools**.

There's nothing wrong with doing it the hard way, but make it easy on yourself when you can.

---

### Post by bernardomh on 2010-02-04
> **djchandler said:**
> Have you tried using **System>Administration>Disk Utility**? I don't remember if it installs by default or not. If it doesn't, it should.

If not, you can find it in **Ubuntu Software Center** under **System Tools**.

There's nothing wrong with doing it the hard way, but make it easy on yourself when you can.

Yes, i have the disk utility. But what should i do there?. The partition is listed and it says that the volume contains a mountable filesystem. How can i configure from there so that it is automatically mounted?

When i press the mount button i get the following error:
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda4 on ext4


Thanx

---

### Post by bernardomh on 2010-02-04
> **bernardomh said:**
> Yes, i have the disk utility. But what should i do there?. The partition is listed and it says that the volume contains a mountable filesystem. How can i configure from there so that it is automatically mounted?

When i press the mount button i get the following error:
Error mounting: mount exited with exit code 1: helper failed with:
mount: only root can mount /dev/sda4 on ext4


Thanx

Heeeeeeey! I just removed the line that i added to the fstab file and clicked on mount, now my partition is mounted on media. I hope that it stays the same the next time i start my computer.
Thank you very much.

---

### Post by Leppie on 2010-02-05
you inverted the mountpoint and fs type in your fstab:
```
/dev/sda4 ext4 /media/ defaults 0 0
```this should've been something like:
```
/dev/sda4 [COLOR=Red]/media/ ext4[/COLOR] defaults 0 [COLOR=Magenta]2[/COLOR]
```also, using 2 at the end makes the system check the partition for errors every so many mounts. this will help prevent data loss ;)

---

