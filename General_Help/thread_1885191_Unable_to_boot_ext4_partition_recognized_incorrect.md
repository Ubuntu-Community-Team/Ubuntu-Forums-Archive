---
title: "Unable to boot: ext4 partition recognized incorrectly as silicon_medley_raid_member"
date: 2011-11-22
forum: General Help
---

### Post by wearetheborg on 2011-11-22
Similar to the problem in [http://ubuntuforums.org/showthread.php?t=1711929](http://ubuntuforums.org/showthread.php?t=1711929)  But for ext4.
 As there, I can mount in live CD using mount -t ext4 Otherwise it gives type as "silicon_medley_raid_member";
 blkid -p on device gives /dev/sda5: VERSION="26161.27241";  TYPE="silicon_medley_raid_member" USAGE="raid"
 wipefs on the device /dev/sda5 returned blank (no output).   
I tried dmraid -E -r on device, but it gave "no raid disks and with names: /dev/sda5"  

Here is the new twist: I also booted using a Scientific Linux 6.0 live dvd,  and there the filesystem is recognized correctly!!!!!!! blkid -p there gave: /dev/sda5: UUID="xxxxxxxx" VERSION="1.0"  TYPE= ext4  USAGE=filesystem

 wipefs on device gave  offset xxxx type: ext4 [filesystem]       UUID: xxxxxxxxxxxxxx   In the SL6 environment, the device mounts without being forced to ext4.

Any suggestions on how to fix this?

---

### Post by wearetheborg on 2011-11-23
Bump.......

---

### Post by wearetheborg on 2011-11-25
Anyone?.....

Pretty please?

---

### Post by oldtimer7777 on 2011-11-25
I suggest upgrading your system to use ext4, as that has solved this issue for other users.

> **wearetheborg said:**
> Similar to the problem in [http://ubuntuforums.org/showthread.php?t=1711929](http://ubuntuforums.org/showthread.php?t=1711929)  But for ext4.
 As there, I can mount in live CD using mount -t ext4 Otherwise it gives type as "silicon_medley_raid_member";
 blkid -p on device gives /dev/sda5: VERSION="26161.27241";  TYPE="silicon_medley_raid_member" USAGE="raid"
 wipefs on the device /dev/sda5 returned blank (no output).   
I tried dmraid -E -r on device, but it gave "no raid disks and with names: /dev/sda5"  

Here is the new twist: I also booted using a Scientific Linux 6.0 live dvd,  and there the filesystem is recognized correctly!!!!!!! blkid -p there gave: /dev/sda5: UUID="xxxxxxxx" VERSION="1.0"  TYPE= ext4  USAGE=filesystem

 wipefs on device gave  offset xxxx type: ext4 [filesystem]       UUID: xxxxxxxxxxxxxx   In the SL6 environment, the device mounts without being forced to ext4.

Any suggestions on how to fix this?

---

### Post by oldfred on 2011-11-25
You do not remove RAID from a partition like sda5,  but from a drive like sda. If you are sure you are not using RAID.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by wearetheborg on 2011-11-26
Yup, never used RAID. I'm not even sure that the laptop has raid capability.

Anyhoo...solved it as follows:

Booted off SL live cd.
Copied over all files from the root partition (cp -a) to external drive.
Deleted /dev/sda5
Created ext4 from deleted space.
Fixed drive device order using fdisk
Copied back files from external drive.
Booted off ubuntu 11.10 live cd and ran Boot-Repair and repaired grub.

---

