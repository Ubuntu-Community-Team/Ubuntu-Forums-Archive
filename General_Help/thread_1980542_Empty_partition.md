---
title: "Empty partition"
date: 2012-05-15
forum: General Help
---

### Post by christovic on 2012-05-15
Hi, I just got a new hard drive yesterday, 2TB, and copied across all the files I needed, into two partitions, that I created in Disk Utility. One was 500GB and the other was 1TB. They were both FAT32, as they needed to be read by Linux, MacOSX and Windows. So I transferred data to the partitions respectively, and when I plugged the hard drive into the mac, it just said there was nothing there at all. Back to the ubuntu machine, and I looked around in disk utility to see the type was FAT 32, but the *partition type* was in Empty (0x00) Tried to change it in the 'Edit partition' Button but no avail. Gparted doesn't recognise them either. Can mount and view the files as normal. Don't want to wipe it and start again, as it took over 7 hours to transfer the data.. Anyone got any ideas?

---

### Post by roelforg on 2012-05-15
Lemme see...
2 TB drive...
1TB + 500GB=1.5TB
1.5TB<2TB
So i think the mac is looking a the remaining 500gb that you didn't allocate.

---

### Post by christovic on 2012-05-15
That would make sense, but even going under the disk utility in the Mac, it shows no partitions on the entire disk. If the *Edit Partition* option worked, I reckon it would read them. Do you have any idea why it's not doing what it's supposed to do?

UPDATE:
Added a small 10GB partition and added some files. The partition type comes up as W95 FAT32, and the Mac can read it.

---

### Post by roelforg on 2012-05-15
> **christovic said:**
> That would make sense, but even going under the disk utility in the Mac, it shows no partitions on the entire disk. If the *Edit Partition* option worked, I reckon it would read them. Do you have any idea why it's not doing what it's supposed to do?

UPDATE:
Added a small 10GB partition and added some files. The partition type comes up as W95 FAT32, and the Mac can read it.

I just remembered something (it has been a long time since i've had to mess with fat/ntfs partitioning so forgive my slow memory), fat32 has a maximum partitionsize... One that's way below 500gb, thus making that partition a corrupted one for a fat implementation that actually checks for that (i don't think linux nor windows care about reading one, only windows cares about creating one).

Plus, i think the mac osx is missing a driver (or whatever you call that for a mac).

---

