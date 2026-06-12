---
title: "How to REALLY wipe a hard drive with Ubuntu???"
date: 2011-08-03
forum: General Help
---

### Post by imhotep531 on 2011-08-03
I'm running Ubuntu 10.04.2 LTS.  The machine is a very recent build and I currently have three HDs attached as follows:

1 x 80GB SATA II - plugged into motherboard with no RAID capability whatsoever
2 x 500GB SATA II - both plugged into a PCI-E card that does have fakeRAID capability but is currently disabled in the card's BIOS in favor of using mdadm instead.

When I run dmraid -r I get this:

/dev/sda: "sil" and "nvidia" formats discovered (using nvidia)!
/dev/sdc: sil, "sil_bhahdcaifbbj", unknown, ok, 976771630 sectors, data@ 0
/dev/sdb: sil, "sil_bhahdcaifbbj", unknown, ok, 976771630 sectors, data@ 0
/dev/sda: nvidia, "nvidia_afgceafe", mirror, ok, 156301486 sectors, data@ 0

/dev/sda is the 80GB drive I mentioned above.  In a former life this drive was part of a RAID 1 array on an ASUS motherboard with built-in fakeRAID capability via the onboard nVidia chipset.  I used this fakeRAID for awhile before switching to the Silicon Image option that also came with the same motherboard.

Now, this drive has been wiped, partitioned, and formatted many times over since being a part of that former system in which it participated in RAID 1 via nVidia and later via Sil.  Somehow Ubuntu is aware of this even though its been wiped over and over.

I'd like to totally blitz this drive of ALL traces of it's former self.  Thus far my efforts to do so using combinations of fdisk, gparted, and mkfs have been unsuccessful.  Everytime I connect this drive it still has some trace of the nVidia and Sil RAID.

How can I REALLY wipe these drives?

---

### Post by OverlordYertle on 2011-08-03
I'm not sure of a way to do it in linux. My friend was having problems wiping his hard drive with windows on it. He used a boot program called [DBan]("http://www.dban.org/") that worked very well at getting rid of a couple of windows files that just wouldnt get cleared away. From what I understand the program just writes 0's in every sector giving it the same status as a brand new hard drive. Though the process can take a few hours to complete. This seems like it would do what you are also trying to accomplish so I hope it helps in some way.

---

### Post by yetiman64 on 2011-08-03
There are 2 tools available on the live cd you can use either shred or dd.

It pays to be very careful with multiple drives and / or partitions and is a good idea to use the command,

```
sudo fdisk -l
```to get the correct drive/partition designation before using either of them (that is a lower case L in the code btw).

[[COLOR=Blue]--Here--[/COLOR]]("http://ubuntuforums.org/showpost.php?p=10685165&postcount=2") is a post where the usage of shred is given for wiping a system, if you wipe an entire drive (by not specifying the partition number) you will need to put a msdos partition table back on it with gparted (also on the live cd).

You can look up the usage of either shred or dd with the commands in a terminal,

```
man shred
```or
```
man dd
```

Edit: note in the instructions linked the --iterations=0 means no overwrites (to keep the time of the job reasonable) it is the "--zero" switch that erases the drive or partition by setting every bit on the drive to a 0 (sometimes called a "factory reset").

---

### Post by imhotep531 on 2011-08-03
Thanks guys much appreciated.

---

### Post by imhotep531 on 2011-08-06
I used the shred command on three SATA II drives, all of which were habitually reporting some kind of RAID that was left over from years prior.  When all attempts to wipe this info from the drives using fdisk, gparted, mkfs, etc,  the shred command succeeded.  Thanks again for the help.

---

### Post by dcstar on 2011-08-08
> **imhotep531 said:**
> 
........
How can I REALLY wipe these drives?

All other methods do not "really wipe" drives apart from this one:
[https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase](https://ata.wiki.kernel.org/index.php/ATA_Secure_Erase)

---

