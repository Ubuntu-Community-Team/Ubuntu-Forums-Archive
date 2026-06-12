---
title: "Extended partition goes past end of drive - help!"
date: 2012-08-04
forum: General Help
---

### Post by nikonian on 2012-08-04
I just fixed my mistake of erasing the first 5MB of my hdd with dd, and now Gparted etc say I have no partition table, so it seems my extended partition is too big, and goes beyond the drive size:

sudo fdisk -l:

```

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders, total 1953525168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x8b3fe527

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *      206848   511999999   255896576    7  HPFS/NTFS/exFAT
/dev/sda2       512000000  1653688304   570844152+   7  HPFS/NTFS/exFAT
/dev/sda3      1653690368  1696698367    21504000   83  Linux
/dev/sda4      1696698423  1953536129   128418853+   f  W95 Ext'd (LBA)
/dev/sda5      1696700416  1940412415   121856000   83  Linux
/dev/sda6      1940414464  1953523695     6554616   82  Linux swap / Solaris

```

Any ideas how I fix?

Please also find attached the first 512 bytes of my disk, saved using dd. Thanks

---

### Post by oldfred on 2012-08-04
First backup partition table and save to another device, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt


Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts is the easiest way. You can also use the sfdisk output, manually edit it to correct size and re-import it. That is why we want backup from sfdisk, just in case.

---

### Post by nikonian on 2012-08-04
> **oldfred said:**
> First backup partition table and save to another device, use your drive for sdX or sda, sdb etc.
sudo sfdisk -d /dev/sdX > parts.txt


Fixparts - Repair broken partition tables (not overlapping issues) & delete Stray gpt data from MBR drives
[http://ubuntuforums.org/showthread.php?t=1705325](http://ubuntuforums.org/showthread.php?t=1705325) 
[http://www.rodsbooks.com/fixparts/](http://www.rodsbooks.com/fixparts/)

Fixparts is the easiest way. You can also use the sfdisk output, manually edit it to correct size and re-import it. That is why we want backup from sfdisk, just in case.


Thank you so much! :D


[EDIT - UPDATE]

You are a kind person, and fixparts just fixed... well, my parts :-)

---

### Post by dcstar on 2012-08-06
> **yeshuaiseverything said:**
> T
You are a kind person, and fixparts just fixed... well, my parts :-)

If it is Solved then MARK THE THREAD!

---

### Post by nikonian on 2012-08-09
> **dcstar said:**
> If it is Solved then MARK THE THREAD!

Okay, but you could have been more polite... and calm.

I shall do now :)

Thanks

---

