---
title: "external hard drive not mounting in ubuntu (bootable flag)"
date: 2012-07-17
forum: General Help
---

### Post by tedaze on 2012-07-17
hello folks,

I have a problem accessing the data on my external hard drive. I  recently did a fresh install but i mistakenly left my external hard  drive plugged in when i did the install. After install was completed,  I tried to access the data on the external hdd,  but it says "no files" but recognizes the fact that it has 290gb of data on  it (it is a 350gb hdd). On my xp laptop, the data was accessible as normal.

I checked the drive with disk utility and it showed that the external hard  drive had a bootable flag, so in "edit partition", I unchecked the  bootable box. Now it will not mount in ubuntu, and also, now my xp  laptop doesn't recognize it whereas before, I could access the data on  the xp machine. In disk utility, it doesn't give me the option to  recheck the bootable box so now i can't access the data in xp as well as ubuntu.

Any ideas on how to fix it?

Thanks very much

---

### Post by drs305 on 2012-07-17
tedaze,

Welcome to the Ubuntu Forums.

It should be a partition that has the boot flag set. Additionally, Ubuntu doesn't use the boot flag, although Windows does.

If Disk Utility doesn't do it, try Gparted. Highlight the partition, then Partition > Edit Flags

Another item you might consider a 'boot flag' issue is which drive is accessed during boot (set by the BIOS) and where the MBR looks for the boot files. If you need to change which drive is booted first by BIOS, make the change in the BIOS settings. If you are having problems booting into Linux or into Windows via the Grub menu, install Boot Repair from your running Ubuntu OS or the LiveCD. Then run the 'Recommended Repair". See the link in my signature line.

---

### Post by tedaze on 2012-07-17
thanks for replying drs305.

I installed gparted and it sees my external hard drive as /dev/sdb (232.89 gb). However, it says the partition is "unallocated". In gparted, under the tab "file system" it says unallocated, under the "size" tab it says "232.89 gb" (the hard drive has a capacity of 250gb), under the "used tab it says "-", it says the same for "unused"  and the "flag" tab is empty.

Any other ideas? I appreciate your help.

cheers

---

### Post by tedaze on 2012-07-17
oh, and by the way, it?'s a NTFS formatted external hard drive, it  never had a bootable os installed on it. The problem is that when I installed ubuntu on my pc, the external hard drive was still plugged in so something on it has been overwritten.

does that make sense?

thanks again

---

### Post by Bucky Ball on 2012-07-17
Not really. Unless you set the flag to format them, no. They would by default be set to 'Don't use' or something like that and nothing should be written to it. 

My external hard drive automounted fine in 10.10 but now I've dropped back to 10.04 LTS I can't get it to mount at all unless I do it manually, so you may have the same problem. It's the release rather than the install. It was a known bug in 10.04 and another release I believe. I'm using FAT32, though, so not quite the same. I'll check if it automounts in 11.04 tomorrow.

---

### Post by tedaze on 2012-07-17
hello folks,

i have some more info: i ran fdsik -l and this info regarding my external hdd appeared:

Disk /dev/sdb: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table

If I try to create a partition table on the device in gparted, will this work or will it reformat my hard drive. I dare not try it in case I make things worse.

thanks again.

---

### Post by Shadius on 2012-07-17
> **tedaze said:**
> hello folks,

i have some more info: i ran fdsik -l and this info regarding my external hdd appeared:

Disk /dev/sdb: 250.1 GB, 250059348992 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000


Disk /dev/sdb doesn't contain a valid partition table

If I try to create a partition table on the device in gparted, will this work or will it reformat my hard drive. I dare not try it in case I make things worse.

thanks again.

Yes, that will format the hard disk drive and you'll lose your data.

---

### Post by sudodus on 2012-07-17
> **Shadius said:**
> Yes, that will format the hard disk drive and you'll lose your data.
+1
Don't edit the partition table!!! That will wipe the data (or at least make them very hard to recover).


In post #1 you wrote that the drive has 350 GB, but in post #3 you wrote that the drive has 250 GB.

Which is correct (or are there 2 different external drives)?

Can ***Windows*** see the partition now? In that case, run Windows and try to repair it with
```
chkdsk /f
```

If neither Windows nor Linux (Ubuntu) can read the drive (or mount the partition and read files, you can use ***Testdisk*** and try to repair the partition and/or file system.

---

### Post by drs305 on 2012-07-17
I agree with sudodus. Run chkdsk from a Windows CD. You may need to do it several times. Often linux applications can not read an NTFS drive when there are errors on the drive and/or partitions. Running a Windows app which finds and repairs these errors will allow subsequent reading by Ubuntu.

---

