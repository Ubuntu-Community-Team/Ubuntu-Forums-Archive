---
title: "Repair external HDD MBR from Ubuntu?"
date: 2010-06-12
forum: General Help
---

### Post by Jammanuser on 2010-06-12
How do I repair an external HDD's MBR from Ubuntu?
I know there are tools for doing this kind of thing from Windows (such as MbrFix), but I want to know if there's anything to do it from Ubuntu.

Thanks in advance.

-Jam Man

:guitar:

---

### Post by cj.surrusco on 2010-06-12
What bootloader do you have installed on the external HDD?

---

### Post by yetiman64 on 2010-06-12
> **Jammanuser said:**
> How do I repair an external HDD's MBR from Ubuntu?
I know there are tools for doing this kind of thing from Windows (such as MbrFix), but I want to know if there's anything to do it from Ubuntu....

Well, it really depends on the nature of the problem you're having as to what tools to use. Could you specify a bit further as to your problem/situation etc?

If you have unwanted bootcode in the MBR the "dd"command can be used to clear it (with great care - byte size of 446 etc) without touching the drives partition tables. However if the partition tables require fixing something like "testdisk" could be used to recover it.

Generally speaking, yes, there are tools to fix an MBR in Ubuntu, but it very much depends on your situation as to what tool you would use. Before running any command though first run ```
sudo fdisk -l
``` (l is a lower case L) to determine the correct device to work on.

---

### Post by Jammanuser on 2010-06-12
> **cj.surrusco said:**
> What bootloader do you have installed on the external HDD?
Well, I currently have a standard MBR (as well as a BootIt NG EMBR "Extended Master Boot Record") on the external Iomega USB HDD.
I have 3 partitions on the HDD:

1. DATA
2. Image Backups
3. PC-BSD

The third partition contains the Unix OS PC-BSD (a desktop version of FreeBSD), and is the partition set to active (hence it contains the boot files). I am able to boot it fine from an entry in the BING boot menu, but I haven't tried yet to boot it straight from the HDD with it first in the boot sequence of the BIOS, though I'm going to try that soon just as soon as I see if testdisk can fix it, and reboot to see if I can see the partitions in XP.

---

### Post by louieb on 2010-06-12
[TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk") Its in the repositories.  Like Mbrfix - very powerful  - it can fix a broken MBR and just like MbrFix it can fubar the system.

---

### Post by Jammanuser on 2010-06-12
> **yetiman64 said:**
> Well, it really depends on the nature of the problem you're having as to what tools to use. Could you specify a bit further as to your problem/situation etc?

If you have unwanted bootcode in the MBR the "dd"command can be used to clear it (with great care - byte size of 446 etc) without touching the drives partition tables. However if the partition tables require fixing something like "testdisk" could be used to recover it.

Generally speaking, yes, there are tools to fix an MBR in Ubuntu, but it very much depends on your situation as to what tool you would use. Before running any command though first run ```
sudo fdisk -l
``` (l is a lower case L) to determine the correct device to work on.
Yeah, using testdisk just occurred to me as well. I'm about to try that now.
As for the nature of my problem, I have 3 partitions on my external HDD (listed in the post above). Obviously, the PC-BSD partition should not be visible from Windows (at least not its filesystem), but the other two partitions are formatted with NTFS, and so they should be visible. Also, the odd thing is, I just did a fresh reinstall of XP today (and haven't installed all the drivers yet), and the first time I plugged up the external HDD, XP recognized the partitions (and even gave the two NTFS ones drive letters), but now it wont see the partitions at all (not even in Disk Management).

I tried "MbrFix /drive 1 fixmbr" in the command-line, and it reported it fixed the mbr, but nothing changed. Also, BING reports that the MBR of that HDD contains all 3 partitions (though the first time I checked it, it didn't, and I had to add them in in BING), but MbrFix just displays an empty partition table when I do:

```
MbrFix /drive 1 /listpartitions
```

And I've tried mounting the HDD in Ubuntu, but it gives a:

> Unable to mount location
Can't mount file

error.

EDIT: Oh, and the first time I noticed that there was a problem with the HDD was when I looked at the BING Partition Work window, and attempted to resize the first partition (on the physical disk, as well as the partition table) into the free space following it, but BING gave me an error saying I should run chkdsk /f on it. So I then entered XP again to do just that, only unfortunately the partitions of the HDD would no longer show up in My Computer, and Disk Management doesn't display any partitions (it claims that the whole HDD is unformatted space). And so I can't run chkdsk on the partition yet until I fix the non-displayable partitions problem in XP.

---

### Post by Jammanuser on 2010-06-12
> **louieb said:**
> [TestDisk - CGSecurity]("http://www.cgsecurity.org/wiki/TestDisk") Its in the repositories.  Like Mbrfix - very powerful  - it can fix a broken MBR and just like MbrFix it can fubar the system.
Yeah, I know about TestDisk and its already installed on my system.
I've used it before, and know its a pretty cool tool, and I'm about to go use it right now.

-Jam Man

:guitar:

---

### Post by Jammanuser on 2010-06-12
And 

sudo fdisk -l

reports the following:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c5a8d58

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2               6        1279    10233405    7  HPFS/NTFS
/dev/sda3           19765       34361   117250402+   f  W95 Ext'd (LBA)
/dev/sda4   *       17216       19764    20474842+  83  Linux
/dev/sda5           19765       20337     4602591   82  Linux swap / Solaris
/dev/sda6           20338       27986    61440561    7  HPFS/NTFS
/dev/sda7           27987       34361    51207156    7  HPFS/NTFS

Partition table entries are not in disk order

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x8f800000

   Device Boot      Start         End      Blocks   Id  System

```
The second HDD ( /dev/sdb ) is the problem one, and fdisk isn't displaying any partitions on it, but I KNOW they exist. :)
Testdisk is analyzing the HDD right now, and so far has displayed the two NTFS partitions. I don't know if it can display HFS partitions or not, which is the filesytem that PC-BSD uses, I believe.

Also note that since I'm using BootIt NG, my MBR partition table changes every time I boot a different entry with a different partition set, thus the info displayed right now by fdisk wouldn't be the same if I was in XP, for example.

EDIT: Ok, Testdisk is now displaying the FreeBSD partition. See attachment.

---

### Post by Jammanuser on 2010-06-12
Ok, nevermind. It seems I was wrong. The "Image Backups" partition (shown as "NEW MBR ENT" in Testdisk) is actually a Fat 32 partition. I guess I forgot I formatted it as that, and thought it was NTFS.
Anyway, I'm going to try to rewrite the bootsector on both of those partitions, leaving only the PC-BSD partition alone in Testdisk.

---

### Post by Jammanuser on 2010-06-12
Yeah, I am able to view all files on all 3 partitions in Testdisk, for those of you who might be doubting me right now... :p
So obviously the filesystems are intact. It must be the bootsectors messed up.

---

### Post by Jammanuser on 2010-06-12
I'll post a copy of meierfra's boot_info_script RESULTS.txt in a second, so everyone can see what my system looks like with ALL partitions included (since BING keeps some hidden away in its EMBR if you have more than 4 primaries on one HDD). 

EDIT: Nevermind...the script is hanging again. Forgot to help Meierfra resolve that problem a while back.

---

