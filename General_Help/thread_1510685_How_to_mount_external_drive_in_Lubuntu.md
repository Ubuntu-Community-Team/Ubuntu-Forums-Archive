---
title: "How to mount external drive in Lubuntu?"
date: 2010-06-15
forum: General Help
---

### Post by geovino on 2010-06-15
How to mount external drive in Lubuntu?

---

### Post by cariboo on 2010-06-15
According to [this]("https://wiki.ubuntu.com/Lubuntu/SubTeams/TestingSubTeam/pcmanfm2Testing") auto-mounting is broken. You have to mount your external drives manually. You can find the device label by opening a terminal just after you have plugged the device in and typing:

```
dmesg | tail -n10
```

You should see something that looks like this:

```
dmesg | tail -n10
[44751.020686] scsi 4:0:0:0: Direct-Access     SanDisk  Ultra Backup     8.32 PQ: 0 ANSI: 0 CCS
[44751.020990] sd 4:0:0:0: Attached scsi generic sg3 type 0
[44751.023579] sd 4:0:0:0: [sdc] 15745023 512-byte logical blocks: (8.06 GB/7.50 GiB)
[44751.024519] sd 4:0:0:0: [sdc] Write Protect is off
[44751.024523] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[44751.024525] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[44751.026669] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[44751.026676]  sdc: **sdc1**
[44751.029420] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[44751.029429] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

I've bolded the device label in the above example. to mount the drive, in the same terminal type:

```
sudo mount /dev/sdc1 /mnt
```

The above command will allow you to access your external drive 
in the /mnt directory.

---

### Post by geovino on 2010-06-16
> **cariboo907 said:**
> According to [this]("https://wiki.ubuntu.com/Lubuntu/SubTeams/TestingSubTeam/pcmanfm2Testing") auto-mounting is broken. You have to mount your external drives manually. You can find the device label by opening a terminal just after you have plugged the device in and typing:

```
dmesg | tail -n10
```

You should see something that looks like this:

```
dmesg | tail -n10
[44751.020686] scsi 4:0:0:0: Direct-Access     SanDisk  Ultra Backup     8.32 PQ: 0 ANSI: 0 CCS
[44751.020990] sd 4:0:0:0: Attached scsi generic sg3 type 0
[44751.023579] sd 4:0:0:0: [sdc] 15745023 512-byte logical blocks: (8.06 GB/7.50 GiB)
[44751.024519] sd 4:0:0:0: [sdc] Write Protect is off
[44751.024523] sd 4:0:0:0: [sdc] Mode Sense: 45 00 00 08
[44751.024525] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[44751.026669] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[44751.026676]  sdc: **sdc1**
[44751.029420] sd 4:0:0:0: [sdc] Assuming drive cache: write through
[44751.029429] sd 4:0:0:0: [sdc] Attached SCSI removable disk
```

I've bolded the device label in the above example. to mount the drive, in the same terminal type:

```
sudo mount /dev/sdc1 /mnt
```

The above command will allow you to access your external drive 
in the /mnt directory.

Thank you.

---

### Post by okos on 2010-06-16
another way to identify all of your disks is 
> sudo fdisk -l

For example
```
sudo fdisk -l

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x120563c4

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         192     1534976    7  HPFS/NTFS
/dev/sda2             192       14667   116269052    7  HPFS/NTFS
/dev/sda3           14667       30402   126389834    5  Extended
/dev/sda5           24234       26171    15558480   83  Linux
/dev/sda6           14667       24234    76847337   83  Linux
/dev/sda7           26171       30292    33104896   83  Linux
/dev/sda8           30292       30402      877568   82  Linux swap 

```
Then create a directory for the mount point.
```
sudo mkdir extdrive
```

Mount drive
```
sudo mount /dev/sda7 extdrive
```

---

