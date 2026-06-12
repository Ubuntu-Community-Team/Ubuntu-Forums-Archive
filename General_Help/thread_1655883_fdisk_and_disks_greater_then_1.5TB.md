---
title: "fdisk and disks greater then 1.5TB"
date: 2010-12-30
forum: General Help
---

### Post by CharlesA on 2010-12-30
Hiya,

I just bought a 3TB drive to use for backups and I'm getting a strange message when I run fdisk to get a listing of the drives.

Here's what fdisk says about the 3TB drive:

```
Disk /dev/sde: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders
Units = cylinders of 16065 * 4096 = 65802240 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000185ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       45600  2930255748   83  Linux
[COLOR="Red"]Partition 1 does not start on physical sector boundary.[/COLOR]

```

I think I can fix it by repartitioning it and aligning the partition to the cylinder, but I am not 100% sure.

The other question I've got is on a 2TB drive, that I thought used 512byte sectors, but I get a warning about it.

```
Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2db1122

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   83  Linux
[COLOR="Red"]Note: sector size is 4096 (not 512)[/COLOR]

```

Any ideas?

---

### Post by QLee on 2010-12-30
[QUOTE=CharlesA]...
```
Disk /dev/sde: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders
Units = cylinders of 16065 * 4096 = 65802240 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000185ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       45600  2930255748   83  Linux
[COLOR=Red]Partition 1 does not start on physical sector boundary.[/COLOR]

```I think I can fix it by repartitioning it and aligning the partition to the cylinder, but I am not 100% sure.[/QUOTE]

All the C/H/S stuff has been "magic" for a while on big drives.

I imagine if you start on sector 64 instead of 1 that error might go away. I'm not sure the error matters anyway.

[QUOTE=CharlesA]The other question I've got is on a 2TB drive, that I thought used 512byte sectors, but I get a warning about it.

...
   ```
Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   83  Linux
[COLOR=Red]Note: sector size is 4096 (not 512)[/COLOR]

```Any ideas?[/QUOTE]

I thought ext4 used 4096.


In my opinion, poster srs5694 is our "resident" expert on disks and partitions, I would trust any replies. You might consider pinging but I don't know if it would be answered. Often is around here somewhere near this timeslice.

Are we sure this is a "beginner" topic?

---

### Post by CharlesA on 2010-12-30
> **QLee said:**
> All the C/H/S stuff has been "magic" for a while on big drives.

I imagine if you start on sector 64 instead of 1 that error might go away. I'm not sure the error matters anyway.

I read a lot of conflicting info about that. I just don't want to lose data due to a improperly set up partition.

> I thought ext4 used 4096.

In my opinion, poster srs5694 is our "resident" expert on disks and partitions, I would trust any replies. You might consider pinging but I don't know if it would be answered. Often is around here somewhere near this timeslice.

I don't know, to be honest. All the drives are running ext4, if that makes a difference. I haven't been able to find any real "answers" if the messages I'm getting are errors, warnings, or just informational.

---

### Post by srs5694 on 2010-12-30
> **CharlesA said:**
> I just bought a 3TB drive to use for backups and I'm getting a strange message when I run fdisk to get a listing of the drives.

Here's what fdisk says about the 3TB drive:

```
Disk /dev/sde: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders
Units = cylinders of 16065 * 4096 = 65802240 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x000185ff

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       45600  2930255748   83  Linux
[COLOR=Red]Partition 1 does not start on physical sector boundary.[/COLOR]

```I think I can fix it by repartitioning it and aligning the partition to the cylinder, but I am not 100% sure.

This warning looks like an fdisk bug to me; your sector size is being reported as 4096 bytes (both physical and logical), so there's no way the partition can begin on anything but a physical sector boundary. This bug is probably being triggered by new and therefore poorly-tested code related to the new "Advanced Format" drives, which use 4096-byte physical sectors and 512-byte logical sectors, but that doesn't seem to be what your drive has.

If you want to be absolutely positive, or just get rid of the warning, you should read [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote for IBM developerWorks and create new partitions that are aligned on multiples of 8 sectors. If you need more help, post the output of "sudo fdisk -lu". Note that last "u"; it improves the precision of data reported by fdisk. The output you posted is hopelessly imprecise.

> The other question I've got is on a 2TB drive, that I thought used 512byte sectors, but I get a warning about it.

```
Disk /dev/sdd: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xa2db1122

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1      243201  1953512001   83  Linux
[COLOR=Red]Note: sector size is 4096 (not 512)[/COLOR]

```Any ideas?

I'm not sure what's triggering this notice. Perhaps your version of fdisk is doing some tests I don't know about to determine the physical sector size when the drive lies about it (as at least some Advanced Format drives do). Please post the output of "cat /proc/scsi/scsi" so we can see what sort of drive you've got and track down the information on it. Also, aligning partitions to 8-sector multiples will protect you against problems, with very little in the way of negative consequences if this is unnecessary.

[quote="QLee"]I thought ext4 used 4096.[/quote]

The fdisk utility doesn't look inside partitions to determine anything about filesystems, so this is irrelevant to the messages displayed by fdisk. It *is* relevant to performance issues, though; the fact that ext2/3/4, and many other modern filesystems, use data structures that are 4096 bytes in size is why partitions must be aligned on 8-sector multiples to get optimum performance on Advanced Format drives. If partitions are improperly aligned, then when Linux tries to write a single 4096-byte filesystem data structure, the drive ends up having to read two sectors, modify parts of both of them, and then write them back. This takes longer than it would to just write one 4096-byte sector.

---

### Post by sammiev on 2010-12-30
I have a few Seagate USB HDs and one of them are a 2TB and the sector size is 4096. Not saying that yours is. GL :)

---

### Post by hawkmage on 2010-12-30
Re-partitioning the 3 TB drive should fix the issud.  One I would highly suggest to repartition it before using it for anything other than testing.  There can be a big performance hit for misaligned writes.  

As for the 2 TB drive you may want to look up the HD specs on the vendors site.  If it is truely a 4k sector and you can repartition it you should do so using the "-b 4096" option on fdisk

---

### Post by CharlesA on 2010-12-30
> **srs5694 said:**
> If you want to be absolutely positive, or just get rid of the warning, you should read [this article](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/) I wrote for IBM developerWorks and create new partitions that are aligned on multiples of 8 sectors. If you need more help, post the output of "sudo fdisk -lu". Note that last "u"; it improves the precision of data reported by fdisk. The output you posted is hopelessly imprecise.

I think I actually read that, since I saw it in another thread on here and it was one of the hits on a google search I did earlier.

The model of that drive is [this one]("http://www.bestbuy.com/site/Seagate+-+FreeAgent+GoFlex+Desk+3TB+External+USB+2.0/3.0+Hard+Drive+-+Black/1361508.p?id=1218252977386&skuId=1361508&st=seagate%20external%203tb&cp=1&lp=1"). I remember reading a [review]("http://www.anandtech.com/show/3858/the-worlds-first-3tb-hdd-seagate-goflex-desk-3tb-review") about it that mentioned something about sector translation or some such thing.

I'll post the output of the fdisk when I get home.

> I'm not sure what's triggering this notice. Perhaps your version of fdisk is doing some tests I don't know about to determine the physical sector size when the drive lies about it (as at least some Advanced Format drives do). Please post the output of "cat /proc/scsi/scsi" so we can see what sort of drive you've got and track down the information on it. Also, aligning partitions to 8-sector multiples will protect you against problems, with very little in the way of negative consequences if this is unnecessary.

That was the first time I saw it, but I don't do an fdisk all that often, and that drive has been partitioned and formatted like that for a while now. *shrug* I'll have to get the exact model of the 2TB drive when I get home, but I think it's [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148417").

> **hawkmage said:**
> Re-partitioning the 3 TB drive should fix the issud.  One I would highly suggest to repartition it before using it for anything other than testing.  There can be a big performance hit for misaligned writes.  

As for the 2 TB drive you may want to look up the HD specs on the vendors site.  If it is truely a 4k sector and you can repartition it you should do so using the "-b 4096" option on fdisk

I repartitioned it this morning and told it to align to cylinder, as I didn't see an option to align by sector in gparted.

---

### Post by srs5694 on 2010-12-30
> **CharlesA said:**
> The model of that drive is [this one]("http://www.bestbuy.com/site/Seagate+-+FreeAgent+GoFlex+Desk+3TB+External+USB+2.0/3.0+Hard+Drive+-+Black/1361508.p?id=1218252977386&skuId=1361508&st=seagate%20external%203tb&cp=1&lp=1"). I remember reading a [review]("http://www.anandtech.com/show/3858/the-worlds-first-3tb-hdd-seagate-goflex-desk-3tb-review") about it that mentioned something about sector translation or some such thing.

Seagate's Web site and PDFs on the drive are annoyingly silent on the issue of sector size. There may be some technical details out there somewhere on the drive, but I don't see them offhand.

That said, I did have a phone conversation a few months ago with a Seagate engineer (a real engineer, not a tech support drone), and he said that the first generation of Seagate 3 TB external disks had 512-byte sectors but used USB interfaces that translated to 4096-byte sectors as a way of bypassing MBR's 32-bit sector addressing limitations. If that's your disk and if everything is working properly, that means that it should have 4096-byte sectors as far as Linux is concerned, and the warning message you've got is bogus.

Nonetheless, partitioning so that the first sector starts at precisely the 1 MiB boundary (sector 256, in your case) can't hurt.

> That was the first time I saw it, but I don't do an fdisk all that often, and that drive has been partitioned and formatted like that for a while now. *shrug* I'll have to get the exact model of the 2TB drive when I get home, but I think it's [this one]("http://www.newegg.com/Product/Product.aspx?Item=N82E16822148417").

Once again, I can't find anything useful on Seagate's Web site. I'm not sure if Seagate has begun shipping anything with 4096-byte sectors; Western Digital was the first, about a year ago, and the other major players have been slower to move to this new technology. Given that your drive is discontinued, it's probably an older technology with conventional 512-byte sectors. That said, it's conceivable that something weird is going on in the USB interface that's confusing fdisk.

> I repartitioned it this morning and told it to align to cylinder, as I didn't see an option to align by sector in gparted.

On disks that use Advanced Format technology, partitioning to cylinder alignment would be a very bad move. I don't think you've got such a drive, but I can't be positive of that. The details of what different tools support has been changing rapidly, so the precise options you've got and best procedures will vary from one version of a utility to the next.

[quote=hawkmage]As for the 2 TB drive you may want to look up the HD specs on the  vendors site.  If it is truely a 4k sector and you can repartition it  you should do so using the "-b 4096" option on fdisk 	[/quote]

The -b option to fdisk overrides the logical sector size value detected by fdisk. This is theoretically useful if something in the chain is so screwed up that fdisk is getting that critical detail wrong, but there's no evidence that this is the case. It looks like you're just seeing one or possibly two bogus warnings. Notably, the sizes of the disks in gigabytes are both correct (or at least reasonable), and the math for everything else seems to work out. If you use -b inappropriately, as I believe it would be for either of your disks, the result is likely to be a damaged partition table and data corruption. That said, if you can find technical specs that say the disk uses 4096-byte sectors, using -b may be in order; but you've got to be careful about this, since as already noted, there can be translations in the USB layer, and you need to use whatever is appropriate for the interfaces that the kernel will be using (probably whatever the USB interface is using, which may not be what the drive itself is using).

---

### Post by CharlesA on 2010-12-30
> **srs5694 said:**
> Seagate's Web site and PDFs on the drive are annoyingly silent on the issue of sector size. There may be some technical details out there somewhere on the drive, but I don't see them offhand.

That said, I did have a phone conversation a few months ago with a Seagate engineer (a real engineer, not a tech support drone), and he said that the first generation of Seagate 3 TB external disks had 512-byte sectors but used USB interfaces that translated to 4096-byte sectors as a way of bypassing MBR's 32-bit sector addressing limitations. If that's your disk and if everything is working properly, that means that it should have 4096-byte sectors as far as Linux is concerned, and the warning message you've got is bogus.

Nonetheless, partitioning so that the first sector starts at precisely the 1 MiB boundary (sector 256, in your case) can't hurt.

That's what I found as well, unfortunately - no info about the disks at all on the Seagate website. In that one review, it mentioned the sector size, and I'm glad that's been confirmed. Thanks.

> Once again, I can't find anything useful on Seagate's Web site. I'm not sure if Seagate has begun shipping anything with 4096-byte sectors; Western Digital was the first, about a year ago, and the other major players have been slower to move to this new technology. Given that your drive is discontinued, it's probably an older technology with conventional 512-byte sectors. That said, it's conceivable that something weird is going on in the USB interface that's confusing fdisk.

It's probably just being confused, as I haven't had any problems with that drive and I thought it had 512byte sectors, as it was one of the older 2TB drives (and I have other 2TB drives that use 512bytes sectors).

> On disks that use Advanced Format technology, partitioning to cylinder alignment would be a very bad move. I don't think you've got such a drive, but I can't be positive of that. The details of what different tools support has been changing rapidly, so the precise options you've got and best procedures will vary from one version of a utility to the next.

Thanks for the info there. I'll repartition the drive to 1MiB and see if the message goes away. If not, then I'll see if I can fill up the drive and see what happens. Hopefully it'll be relatively fast since it's got a USB 3 interface.

EDIT: I checked an fdisk -l with the 3TB drive removed and that notification that the sectors were 4096 instead of 512 wasn't listed under the 2TB drive. I guess that it was just a notification of the newer format drive. At least that solved that mystery. :)

---

### Post by CharlesA on 2010-12-30
Ok. I think I figured it out (somehow).

I originally created a GPT partition table on the drive before creating the partition. After doing so, running fdisk would yield the "Not aligned" error.

Checking it with parted showed that it was aligned correctly.

However, on a hunch, I switched it back to an msdos partition table and it seems to have been able to create a 2.73TiB partition (which as far as I know isn't possible) unless it's due to it using 4096 byte sectors.

Guess I'll just run with it and see how it goes.

Here's what it looks like with an msdos partition table:
```
charles@thor:~$ sudo fdisk -lu /dev/sde
Note: sector size is 4096 (not 512)

Disk /dev/sde: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00021a47

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1             256   732566527  2930265088   83  Linux
```

Here's what it said when I used a GPT partition table:

```
charles@thor:~$ sudo fdisk -lu /dev/sdf

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! The util fdisk doesn't support GPT. Use GNU Parted.

Note: sector size is 4096 (not 512)

Disk /dev/sdf: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1   732566644  2930266576   ee  GPT
Partition 1 does not start on physical sector boundary.

```

Things that make you go Hmm...

Also note: I ran into this when running parted on Ubuntu 10.04.1:

```
charles@thor:~$ sudo parted /dev/sdf
Warning: Device /dev/sdf has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.
```

Apparently version 2.2 doesn't support 4096 sectors very well, I used 2.3 from the gparted site.

Guess I'll just use an msdos partition table and leave it at that.

---

### Post by sammiev on 2010-12-30
Your seagate 2TB is the exact same as mine and mine has a sector size of 4096. Working great I must add. GL :)

---

### Post by CharlesA on 2010-12-30
> **sammiev said:**
> Your seagate 2TB is the exact same as mine and mine has a sector size of 4096. Working great I must add. GL :)
Checked both mine and they have a sector size of 512. *shrugs*

They work fine. :)

---

### Post by srs5694 on 2010-12-31
> **CharlesA said:**
> Ok. I think I figured it out (somehow).

I originally created a GPT partition table on the drive before creating the partition. After doing so, running fdisk would yield the "Not aligned" error.

This is almost certainly a coincidence. If you correctly convert from GPT to MBR, there will be no traces of GPT left behind, and any alignment issues will be caused by whatever MBR partitioning tool you used.

> However, on a hunch, I switched it back to an msdos partition table and it seems to have been able to create a 2.73TiB partition (which as far as I know isn't possible) unless it's due to it using 4096 byte sectors.

If this is the drive whose data you report below, it's 3.0005821 TB (2.729013562 TiB) in size, so with rounding, a 2.73 TiB partition is certainly possible.

> Here's what it looks like with an msdos partition table:
```
charles@thor:~$ sudo fdisk -lu /dev/sde
Note: sector size is 4096 (not 512)

Disk /dev/sde: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00021a47

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1             256   732566527  2930265088   83  Linux
```Here's what it said when I used a GPT partition table:

```
charles@thor:~$ sudo fdisk -lu /dev/sdf

WARNING: GPT (GUID Partition Table) detected on '/dev/sdf'! [COLOR=Red]The util fdisk doesn't support GPT. Use GNU Parted.[/COLOR]

Note: sector size is 4096 (not 512)

Disk /dev/sdf: 3000.6 GB, 3000592977920 bytes
255 heads, 63 sectors/track, 45600 cylinders, total 732566645 sectors
Units = sectors of 1 * 4096 = 4096 bytes
Sector size (logical/physical): 4096 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1               1   732566644  2930266576   ee  GPT
Partition 1 does not start on physical sector boundary.

```Things that make you go Hmm...

Aside from verifying that the protective MBR part of the GPT data structures is correct, fdisk is useless with GPT disks. As the notice I've highlighted in red says, you should use GNU Parted or (not mentioned) my own GPT fdisk (gdisk) instead. Those utilities give information on the GPT data structures.

It looks to me like your latest MBR partitioning job puts the start of the first partition on sector 256. It's unclear, since you used the less precise cylinder units before, but it was probably on sector 63 or some such in your original partitioning scheme. This difference would trigger the (presumably erroneous) warning about alignment originally but not now.

The warning in the GPT case was because GPT requires a protective MBR that starts on sector 1 and ends at the last sector of the disk (or at sector 2^32-1, if this is smaller). Even if sector 1 isn't aligned in the normal way, this is a requirement of GPT, and it doesn't matter, since this partition isn't real; it just exists to keep MBR partitioning tools from messing with the disk. The real partitions are defined in GPT structures, which Linux fdisk can't read.

> Also note: I ran into this when running parted on Ubuntu 10.04.1:

```
charles@thor:~$ sudo parted /dev/sdf
Warning: Device /dev/sdf has a logical sector size of 4096.  Not all parts of GNU Parted support this at the moment, and the working code is HIGHLY EXPERIMENTAL.
```Apparently version 2.2 doesn't support 4096 sectors very well, I used 2.3 from the gparted site.

Yes, that's one of many areas where libparted is only now catching up with current hardware. I suggest using my gdisk for using GPT on disks with other than 512-byte sectors. The standard Linux fdisk handles this task fine for MBR disks.

---

### Post by CharlesA on 2010-12-31
Thanks for the info about how GPT partitions are set up, srs5694. That helps a bit. :)

I just find it strange that the other GPT partition I have isn't causing fdisk to flip out:

```
charles@thor:~$ sudo fdisk -lu /dev/sdb

WARNING: GPT (GUID Partition Table) detected on '/dev/sdb'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sdb: 4000.6 GB, 4000627818496 bytes
255 heads, 63 sectors/track, 486381 cylinders, total 7813726208 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1  4294967295  2147483647+  ee  GPT

```

Granted, that one is on a 4TB RAID-5 Array, and the disks in use are 512bytes sector ones, but I think that's the only difference.

I guess the message I am getting from fdisk with the other drive is erronious, and (probably) due to the fact that the 3TB drive is using 4096 byte sectors.

Is gpdisk in the repos?

---

### Post by srs5694 on 2010-12-31
Yes, clearly it's a bug in whatever code is generating the error message; there's probably a test for the disk size or sector size or something that's not been properly thought out.

Don't worry about it; it's bogus.

GPT fdisk is in the repositories, but it's hopelessly out of date. Download it from [its Sourceforge page.](http://sourceforge.net/projects/gptfdisk/files/)

---

### Post by CharlesA on 2010-12-31
I'm going to convert the 3TB drive back to a GPT partition structure, I've got about 2TB worth of data on it, but I was just testing it. :)

Thanks again.

I'll mark the thread as solved.

---

