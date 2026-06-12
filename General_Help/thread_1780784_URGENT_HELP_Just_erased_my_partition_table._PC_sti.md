---
title: "URGENT HELP: Just erased my partition table. PC still ON"
date: 2011-06-12
forum: General Help
---

### Post by Kalma on 2011-06-12
Hi there,

I made a mistake using Gparted. Instead of erasing the partition of a USB Stick I wanted to use to install Xubuntu on, I have erased the HDD Partition Table. I didn't turn off my PC, so I can still use it and when running Disk Utility all disks and partitions are there. Nevertheless, I think they won't after I turn the PC off.

I am using Testdisk now, but it doesn't find all partitions using the Quick Search. Now I am making a Deeper Search (it is at 7 % after 3 hours...). I have also tried to use Gparted again to re-build the partition table. The problema I found is that the Ubuntu installation asks for MB (1000 KB = 1000 Bytes), but Gparted requests for MiB (1024 Kb = 1024 bytes). For instance, my swap drive is 4000 MB = 3096,25 MiB, but Gparted doesn't handle decimals...

Since everything is still there... Is there a way to re-write the partition table? Is there another tool I can use to introduce either MB's or MiB with decimal parts?

My configuration:

- 2 HDD 500 Gb in RAID0
- Ubuntu 10.04 LTS
- Partitions:
  1. /      Ext3     10 Gb
  2. Windo$ NTFS     96 Gb
  3. Data   NTFS    791 Gb
  4. /home  Ext3     99 Gb
  5. swap             4 Gb

Any help will be welcome. I'm desperated...

---

### Post by pqwoerituytrueiwoq on 2011-06-12
are you sure it let you do that?

i see you are using raid 0 does gparted show that as 2 or 1 disks

if it is 2 you could just copy the other disk to the other one (has never used raid)

---

### Post by Kalma on 2011-06-12
Thank you for your prompt reply.

Yes, It let me do it... if I open Testdisk it says my partition table is empty. Same says Gparted. When you have a RAID 0 and you open Gparted,  it shows a "fake" disk which is as big as the addition of the two physical HDD (in my case 1 Tb). Now, it only shows the two disks (500 Gb each) and no partition on any one of them. I can not copy one disk on the other or I would lose all data.

---

### Post by tredegar on 2011-06-12
I don't think you can recover a deleted partition table unless you have a record of *exactly* how the partitions were originally set up.

If disk utility is showing partitions, maybe they are still there or still in memory somewhere ...
What is the output of ```
sudo fdisk -l
```

I think the first thing you should do is make a backup of ALL of **/home** and any other personal data you feel is important (as opposed to OS data, which can easily be reinstalled) before anything else bad happens.

Make sure this backup includes the "hidden" **.**directories & **.**files

Then, and only then should you try to recover your partition table, if it is indeed lost.

---

### Post by pqwoerituytrueiwoq on 2011-06-12
i would guess you are running off the cache then
to prove this you can change the theme (to one you have not used this session)
if it does not work (or works wrong eg missing graphics) you are using the cache
if i recall correctly raid 0 makes both disk a copy of one another to increase speed by having 2 copies of everything to read at the same time
if testdisk can read the old partition table you can restore it to the other 500gb hdd and then copy the recovery to the other disk

---

### Post by tredegar on 2011-06-12
I have been poking around. This is worth a try:
```
cat /proc/partitions
```

---

### Post by Kalma on 2011-06-12
Thank you again.

Raid0 configures two disks as if you had only one. There is no imaging techniques involved in Raid 0. I believe the RAID is not the problem (although it complicates some solutions, indeed). 

I have already saved all relevant data and I amn now running Testdisk. In the Quick Search option it find 3 of the 5 partitions (the 3 primary ones, since the last 2 are logical partitions within a extended partition. Now I am making a Deepest Search, but it is really slow and I have no guarantee (nor hope) on the result.

If I run fidsk -l, it says "sda can not be read" (sorry for the translation, my OS is in spanish).

I think the partition table information is somehow on memory until I turn my PC off... If I just could find a way to use that information to re-create the partition table, I think it would solve the problem.

---

### Post by Kalma on 2011-06-12
Sorry, I didn't see your last post.

Yes, all the information is there... but I still don't know how to use it.

What I am trying now is:

- Testdisk could only find 3 of the 5 partitions (the 3 primary ones, but not the extended). I have written that information on my disk (something is something).
- I have rebooted, using Live CD
- My 3 partitions are there and they are correct (Ubuntu /, Windo$ and Data).
- Now I have a non-used space on my disk, which corresponds to my lost partitions.
- Since the Ubuntu installation allows me to introduce MB (instead of MiB in Gparted), I will do the following:
1. backup my / partition
2. Install Ubuntu, creating the same partition structure I had before. I lost /home and swap. Then I will choose to mount /home on the same place, but no formatting.
3. Restore the previous backup.

In result, I should have the same partition structure as before. The old information restored on / and a usable and non-erased /home partition... hopefully.

I will let you know it this works, since it can be a good workaround for some other people.

---

### Post by Kalma on 2011-06-12
It worked!!! You may imagine my relief!!!

This solution I proposed is good in case you know the partitions size before you erase them. It is worth to always backup it. I will do it right now!

Thanks everybody!!!

---

### Post by oldfred on 2011-06-12
I found the post where someone else had a similar issue:

If not rebooted, use fdisk to manually recreate table posts by srs5694 post34:
[http://ubuntuforums.org/showthread.php?t=1668247](http://ubuntuforums.org/showthread.php?t=1668247)

Backup partition table to text file & save to external device.
sudo sfdisk -d /dev/sda > PT.txt

Parted also has a rescue mode if you know the range that a partition was in.
Use parted rescue to restore missing partition
[http://ubuntuforums.org/showthread.php?t=1775331](http://ubuntuforums.org/showthread.php?t=1775331)

---

### Post by pqwoerituytrueiwoq on 2011-06-12
congratulations glad to here the recovery worked

---

### Post by Kalma on 2011-06-13
Thanks a lot for the advice and support...

The problem is, having RAID 0, fdisk doesn't properly work. Instead, I found the right partition structure in two places (because I didn't turn the PC off):

- Disk Utility (expressed in Gb and bytes)
- cat /proc/partitions (expressed in sectors)

The problem was how to use this information, since Gparted only handles MiB, and not sectors.

I think it is something that should be changed somehow: Ubuntu installation works with MB, then Gparted works with MiB... It doesn't match!

I believe a good suggestion for Gparted would be to also accept MB and sectors to define partitions.

Now I will back up the partition table. I found a post which recommends using dd command to copy the first disk sector (MBR). The point is that I don't know if I have to backup the /dev/sda first sector or the RAID first sector (the RAID root is on /dev/mapper/sil_aiabbjcga). I will copy both, but the result is unsure.

---

### Post by mastablasta on 2011-06-13
i am not sure about RAID0 setup but in windows ther eis a utility called partition doctor where you can restore and recover deleted partitions. 
 
I had to use it once as some process (i think it was Filezilla update) stopped and i had to reset as it froze the computer. upon reset 2 partitions were missing (deleted). however the main one with OS was still working. so i found this programme and restored the deleted partitions. point and click, easy to understand GUI no manual neded. how come gparted doesn't do this? are you sure it doesn't have restore function?

---

### Post by Kalma on 2011-06-13
Hi again,

yes Gparted does have that feature when using Gparted Rescue Live CD. The problem is RAID 0, I guess. It only found 3 of my 5 partitions (same result than Testdisk). Then I had to re-create them manually, because I found no other alternative to do it automatically.

Another option could've been using some other Windo$ tools (there are many), but I was very reluctant to use it. I wanted to use just Ubuntu to solve the problem (the opposite means Ubuntu is inferior). My Windo$ is only for games... and it will be on my PC only meanwhile the main games are not released on Ubuntu. Once the game developers decide to distribute their games on Ubuntu as well... Bye Bye Windo$ for ever!!!

Have a nice day!!!

---

