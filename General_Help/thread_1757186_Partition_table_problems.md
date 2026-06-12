---
title: "Partition table problems"
date: 2011-05-13
forum: General Help
---

### Post by Strigoides on 2011-05-13
Hi,
I was using Gparted through Parted Magic to resize some of my partitions, when part way through moving one to the right, I got an error; "Error: Invalid partition table on /dev/sda-- wrong signature 250a". After that the whole hard drive showed up as unallocated space. I think it is an instance of this bug: [http://gparted-forum.surf4.info/viewtopic.php?id=14199](http://gparted-forum.surf4.info/viewtopic.php?id=14199), as I was using a fairly old version of Parted Magic. However, when I restarted my computer, I was able to boot into Windows, Arch. and Ubuntu without any problems or loss of data.
 Now when I try to run Gparted, I get a different error; "Can't have a partition outside disk" Based on my fdisk -l output, I think this is because /dev/sda2 is one cylinder over the size of my hard drive. When I run sfdisk -d, I get another warning; "Warning: extended partition does not start at a cylinder boundary. DOS and Linux will interpret the contents differently." I am somewhat confused as to what to do to solve this problem with my partition table

Full output of fdisk and sfdisk:
"fdisk -l";
```
Warning: ignoring extra data in partition table 8
Warning: ignoring extra data in partition table 8
Warning: ignoring extra data in partition table 8

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a96a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16026   128723936+   7  HPFS/NTFS
/dev/sda2           21683       30402    70030336   83  Linux
/dev/sda3           16980       21683    37777409    5  Extended
/dev/sda4   *       16026       16980     7665664   83  Linux
/dev/sda5           17990       18598     4882432   82  Linux swap / Solaris
/dev/sda6           16980       17990     8112128   83  Linux
/dev/sda7           18598       19703     8872960   83  Linux
/dev/sda8   ?      141802      261306   959918725   69  Unknown

Partition table entries are not in disk order

```"fdisk -lu":
```
Warning: ignoring extra data in partition table 8
Warning: ignoring extra data in partition table 8
Warning: ignoring extra data in partition table 8

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders, total 488397168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a96a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   257447935   128723936+   7  HPFS/NTFS
/dev/sda2       348336128   488396799    70030336   83  Linux
/dev/sda3       272781310   348336127    37777409    5  Extended
/dev/sda4   *   257447936   272779263     7665664   83  Linux
/dev/sda5       289007616   298772479     4882432   82  Linux swap / Solaris
/dev/sda6       272781312   289005567     8112128   83  Linux
/dev/sda7       298774528   316520447     8872960   83  Linux
/dev/sda8   ?  2278036316  4197873765   959918725   69  Unknown

Partition table entries are not in disk order

```/dev/sda1 is my Windows XP partition
/dev/sda2 is my /home partition
/dev/sda3 is an extended partiton
/dev/sda4 is my Ubuntu / partition
/dev/sda5 is swap space
/dev/sda6 and /dev/sda7 are Arch and an LFS partition, I can't remember which is which
and I don't know what /dev/sda8 is, I don't think it was on there when I was using Gparted, and it is clearly well over the end of the drive

"sfdisk -d":
```
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=257447873, Id= 7
/dev/sda2 : start=348336128, size=140060672, Id=83
/dev/sda3 : start=272781310, size= 75554818, Id= 5
/dev/sda4 : start=257447936, size= 15331328, Id=83, bootable
/dev/sda5 : start=289007616, size=  9764864, Id=82
/dev/sda6 : start=272781312, size= 16224256, Id=83
/dev/sda7 : start=298774528, size= 17745920, Id=83
/dev/sda8 : start=2278036316, size=1919837450, Id=69
/dev/sda9 : start=2261845235, size=1768448873, Id=73
/dev/sda10: start=2093353307, size=1769173865, Id=7a
/dev/sda11: start=2278295628, size=1936617331, Id=65
```"parted /dev/sda print":
```

Error: Can't have a partition outside the disk!

```Thanks

---

### Post by srs5694 on 2011-05-13
First, don't worry about the "does not start on a cylinder boundary" or "partition table entries are not in disk order" messages. The first of those relates to the obsolete practice of starting partitions on "cylinder" boundaries, which have been convenient fictions for the last two decades or so, but which are no longer convenient. Modern tools now begin partitions on 1 MiB boundaries instead, which improves performance with some types of modern disks. The "not in disk order" message is also unimportant, since computers are good at keeping track of such things; it's just a message to alert you to that fact, since humans are easily confused.

What you do have is a serious problem in partitions 8-11. Your fdisk output shows that fdisk doesn't even see beyond partition 8, it complains about "extra data in partition table 8," and it shows partition 8 as having impossible start and end points. Your sfdisk output shows the same impossible partition 8, along with three more impossible partitions (9, 10, and 11).

Considering through partition 7, I don't see any big gaps or big chunks of unallocated space, although I might be missing something. Thus, I'm inclined to believe that some data corruption crept in that created a bogus partition 8 (through 11, by the means that sfdisk uses to read the partitions). My recommendation is therefore to go into fdisk, delete partition 8, and save your partition table. With any luck, that will fix your problems. You should, however, thoroughly check all your partitions (both with tools like fsck or CHKDSK and by manually inspecting the partitions to look for oddities like missing files or files with bizarre names). You should also check as many files as you can stomach to be sure they contain valid and correct data. In fact, if you backed up your data before beginning this operation, it might be best to just wipe the partition you were resizing/moving and restore it from the backup. The type of error you report can easily result in data corruption that might not be immediately apparent. Perhaps you got lucky and all your files are intact -- or maybe some file is damaged. If so, Murphy's Law says it'll be supporting tax documents, so when you go to print them out you'll get photos of your dog rather than the document that'll save you from a fine!

---

### Post by Strigoides on 2011-05-13
Thanks for the response. I ran chkdsk on my Windows partition and it found a few errors, but after running fsck on all the other partitions, I'm pretty sure they are okay. I used fdisk to delete /dev/sda8, but my sfdisk -d output still includes /dev/sda8. although the id, size and start position has changed
fdisk -l:
```

Warning: ignoring extra data in partition table 7

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008a96a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       16026   128723936+   7  HPFS/NTFS
/dev/sda2           21683       30402    70030336   83  Linux
/dev/sda3           16980       21683    37777409    5  Extended
/dev/sda4   *       16026       16980     7665664   83  Linux
/dev/sda5           17990       18598     4882432   82  Linux swap / Solaris
/dev/sda6           16980       17990     8112128   83  Linux
/dev/sda7           18598       19703     8872960   83  Linux

Partition table entries are not in disk order

```sfdisk -d:
```

Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=257447873, Id= 7
/dev/sda2 : start=348336128, size=140060672, Id=83
/dev/sda3 : start=272781310, size= 75554818, Id= 5
/dev/sda4 : start=257447936, size= 15331328, Id=83, bootable
/dev/sda5 : start=289007616, size=  9764864, Id=82
/dev/sda6 : start=272781312, size= 16224256, Id=83
/dev/sda7 : start=298774528, size= 17745920, Id=83
/dev/sda8 : start=2218609930, size=1768448873, Id=73

```

---

### Post by srs5694 on 2011-05-13
It looks like fdisk linked /dev/sda7 to what had been /dev/sda9 when you deleted /dev/sda8. Ordinarily, this would be perfectly correct, but for whatever reason fdisk is now refusing to display the new /dev/sda8, so you can't delete it with fdisk. Thus, I recommend you do it with sfdisk instead:


[LIST=1]
[*]Type "sudo sfdisk -d /dev/sda > parts.txt" in a terminal window.
[*]Copy parts.txt to a USB flash drive, floppy drive, or whatever for safekeeping, in case things go south.
[*]Edit the original copy of parts.txt in a text editor. Delete the entry for /dev/sda8. Make no other changes to it.
[*]Type "sudo sfdisk -f /dev/sda < parts.txt" (referring to the parts.txt copy you edited). This should write a clean partition table back to the disk.
[*]Reboot.
[/LIST]


With any luck, that'll clear up the trouble. If it doesn't, you could try my [FixParts]("http://www.rodsbooks.com/fixparts") program: Launch it on the disk ("sudo fixparts /dev/sda"), verify that your partitions are all intact with "p" (if they're not, exit with "q"), then save the partitions with "w". I recommend you try the sfdisk solution first, though, because I don't know how FixParts will respond to whatever bogus data is on the disk; I can clearly see from the output you've posted how sfdisk reacts, and aside from the improper /dev/sda8 entry, it looks OK to me, so you've just got to save a cleaned-up version with sfdisk. FixParts might correct the problem even more easily (ideally, it should automatically delete the bogus [noparse]/dev/sda8);[/noparse] or it might crash or misinterpret the partition table in some other unpredictable way.

---

### Post by Strigoides on 2011-05-13
I tried the steps you suggested, but entering "sudo sfdisk -f /dev/sda < parts.txt" spits out this error message, and leaves the partition table unchanged:
```

Checking that no-one is using this disk right now ...
OK

Disk /dev/sda: 30401 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Old situation:
Units = cylinders of 8225280 bytes, blocks of 1024 bytes, counting from 0

   Device Boot Start     End   #cyls    #blocks   Id  System
/dev/sda1          0+  16025-  16026- 128723936+   7  HPFS/NTFS
/dev/sda2      21682+  30401-   8719-  70030336   83  Linux
/dev/sda3      16979+  21682-   4704-  37777409    5  Extended
/dev/sda4   *  16025+  16979-    955-   7665664   83  Linux
/dev/sda5      17989+  18597-    608-   4882432   82  Linux swap / Solaris
/dev/sda6      16979+  17989-   1010-   8112128   83  Linux
/dev/sda7      18597+  19702-   1105-   8872960   83  Linux
/dev/sda8   ? 138102+ 248182- 110081- 884224436+  73  Unknown
        start: (c,h,s) expected (1023,254,63) found (361,99,40)
        end: (c,h,s) expected (1023,254,63) found (378,115,37)
Warning: given size (17745920) exceeds max allowable size (0)
cannot build surrounding extended partition

sfdisk: bad input

```

---

### Post by srs5694 on 2011-05-13
It looks like you didn't edit the parts.txt file, or perhaps referred to the copy you didn't edit. Please review the instructions and input the correct file.

---

### Post by Strigoides on 2011-05-14
I checked it again, and it still doesn't work. To confirm, this is the original parts.txt file:
```


# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=257447873, Id= 7
/dev/sda2 : start=348336128, size=140060672, Id=83
/dev/sda3 : start=272781310, size= 75554818, Id= 5
/dev/sda4 : start=257447936, size= 15331328, Id=83, bootable
/dev/sda5 : start=289007616, size=  9764864, Id=82
/dev/sda6 : start=272781312, size= 16224256, Id=83
/dev/sda7 : start=298774528, size= 17745920, Id=83
/dev/sda8 : start=2218609930, size=1768448873, Id=73

```And the edited parts.txt file:
```

# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=257447873, Id= 7
/dev/sda2 : start=348336128, size=140060672, Id=83
/dev/sda3 : start=272781310, size= 75554818, Id= 5
/dev/sda4 : start=257447936, size= 15331328, Id=83, bootable
/dev/sda5 : start=289007616, size=  9764864, Id=82
/dev/sda6 : start=272781312, size= 16224256, Id=83
/dev/sda7 : start=298774528, size= 17745920, Id=83

```It seems to sometimes come up with the error; "sfdisk: bad input", and sometimes; "sfdisk: long or incomplete input line - quitting"

I have also tried running:
```

sfdisk -f /dev/sda << EOF
> # partition table of /dev/sda
> unit: sectors
> 
> /dev/sda1 : start=       63, size=257447873, Id= 7
> /dev/sda2 : start=348336128, size=140060672, Id=83
> /dev/sda3 : start=272781310, size= 75554818, Id= 5
> /dev/sda4 : start=257447936, size= 15331328, Id=83, bootable
> /dev/sda5 : start=289007616, size=  9764864, Id=82
> /dev/sda6 : start=272781312, size= 16224256, Id=83
> /dev/sda7 : start=298774528, size= 17745920, Id=83
> EOF

```to confirm that I am using the right file, and it still comes up with the same output as in my last post

---

### Post by srs5694 on 2011-05-14
That's so weird that I went and experimented with it. I've discovered a bug in sfdisk; it seems to have problems when the logical partitions are out of order, as yours are (note that /dev/sda6 begins before /dev/sda5). I therefore suggest you try one of two things (do whichever sounds more comfortable to you):

Option 1:

Use my [FixParts](http://www.rodsbooks.com/fixparts) program, as outlined earlier:


[list=1]
[*]Download and install FixParts from [its SourceForge page,](http://sourceforge.net/projects/gptfdisk/files/gptfdisk/0.7.1/fixparts-binaries/) or install the gptfdisk package for your version of Ubuntu from the relevant OpenSUSE Build Service (OBS) link, as described in the "Downloading GPT fdisk from OBS" section [of this page.](http://nessus.rodsbooks.com/gdisk/download.html) (The fixparts package has just FixParts; the gptfdisk package has fixparts, gdisk, and sgdisk, but you probably don't need the latter two programs.)
[*]Type "sudo fixparts /dev/sda".
[*]In FixParts, type "p" to verify that all your primary and logical partitions are present and listed as either primary or logical (not omitted), except of course for the bogus one. Your extended partition will *not* appear in the list. If anything seems wrong, type "q" to exit without saving changes.
[*]In FixParts, type "w" to save your partition table.
[/list]


Option 2:


[list=1]
[*]Load your modified parts.txt file back into a text editor.
[*]Use cut-and-paste operations to reverse the order of /dev/sda5 and /dev/sda6.
[*]Edit the /dev/sda5 entry so that it's identified as /dev/sda6.
[*]Edit the original /dev/sda6 entry so that it's identified as /dev/sda5. You should now have /dev/sda5 and /dev/sda6 in order.
[*]Save your changes.
[*]Type "sudo sfdisk -f /dev/sda < parts.txt", as before.
[/list]


In theory, either of these procedures should work. In practice, it's conceivable you'll run into further problems of one sort or another. Both of them reverse the order of two of your logical partitions, which could affect the bootability of one of your Linux installations if you refer to devices by device filename rather than by UUID or label (as in /dev/sda6 rather than UUID={long UUID value}). Thus, you might want to check the /etc/fstab in your Arch installation before you reboot and make an appropriate adjustment, if necessary. (The swap reference will also change, but is less critical.)

If you try one of those procedures and it doesn't work, try the other one.

---

### Post by Strigoides on 2011-05-14
I tried option 1, and fixparts gave me the following error;
```

FixParts 0.7.1

Loading MBR data from /dev/sda
Unable to seek to 2192618760! Aborting!
MBR signature in logical partition invalid; read 0xAEE1, but should be 0xAA55
```
So I tried option 2, and it worked like a charm! I haven't tried booting  into Arch yet, but I'm not too worried about it as I haven't used it  for a while. Gparted starts up fine now, with /dev/sda5 and 6 showing as  unknown file systems, with the warning;
```
Unable to detect file system! Possible reasons are:
-The file system is damaged
-The file system in unknown to GParted
-There is no file system available (unformatted)
```Is there any way to set the file system type without reformatting, or should I just format /dev/sda6 to swap, and  /dev/sda5 to ext3? Since before I changed the order, /dev/sda5 was swap  space, and /dev/sda6 had an LFS install on it.

---

### Post by srs5694 on 2011-05-15
At least you're making progress!

You could try blkid as a diagnostic, as in:

```

sudo blkid /dev/sda5
sudo blkid /dev/sda6

```

I don't hold out much hope that this would tell you anything, though, if GParted can't identify the filesystems. You could also try running e2fsck on both of them:

```

sudo e2fsck /dev/sda5
sudo e2fsck /dev/sda6

```

I'd expect that to work only on /dev/sda5, since that's the one that *should* now be ext3fs; and if GParted can't detect the filesystem, it could be damaged beyond repair.

If you're willing to discard those installations, you can of course create new filesystems on those partitions or just delete them entirely and plan to use the space in some other way in the future; that's a judgment call on your part.

If you want to recover the data on those partitions and can't seem to do it with those methods, you could try backing up your latest parts.txt (just in case of more trouble), deleting the partitions that can't be detected, and using [TestDisk](http://www.cgsecurity.org/wiki/TestDisk) to try to recover the partitions. I'm suggesting this based on the assumption that the partition definition may have been damaged, shifting its start point in such a way that filesystem detection isn't working. If that's the case, TestDisk might be able to find the lost filesystem. OTOH, if the filesystem data have been so badly damaged that fsck can't recover the filesystem, TestDisk will be a waste of time.

If you have problems recovering your swap space, the easiest approach is indeed to re-create it with mkswap or the equivalent GUI options in GParted. Be aware that you may have to update your /etc/fstab file, since mkswap will generate a fresh UUID value, and Ubuntu references swap space by UUID value by default.

---

### Post by Strigoides on 2011-05-15
I ran e2fsck from Parted Magic, since it seemed to think that /dev/sda5 was busy from Ubuntu, and it seems to have fixed the partition. I then remade the swap partition using mkswap. Everything seems to be fine now.
Thanks for all the help. Do you have any idea what caused this in the first place? I thought it might have been that bug I mentioned in my first post, but maybe not. Any suggestions on how to avoid this problem in the future would be appreciated

EDIT:
I had a look at fstab, and it seems to point to "/dev/mapper/cryptswap1" as the swap partition location. Do I need to change this? Or should "cryptswap1" point to the right location?

Here is my fstab:
```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda4 during installation
UUID=da7b48da-1d64-49e6-a49a-f8baae9b5a19 /               ext4    errors=remount-ro 0       1
# /home was on /dev/sda2 during installation
UUID=4fdebff7-6e2b-4b9c-b4e8-88e0646d5af5 /home           ext4    defaults        0       2
# /windows was on /dev/sda1 during installation
UUID=72F45103F450CACD /windows        ntfs    defaults,umask=007,gid=46 0       0
# swap was on /dev/sda5 during installation
#UUID=1085a5b3-b93b-4614-9f23-14878a7af674 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

```

---

### Post by srs5694 on 2011-05-15
I don't know anything about specific bugs that might have caused this problem, and so I also don't have any advice about specific measures to take to avoid such bugs. I can, however, give you advice to protect yourself: Back up your data! Partition table data can be backed up quite easily by using sfdisk, as you've been doing as part of your recovery efforts; just store the parts.txt file (perhaps renamed to something more descriptive, like parts-sda.txt) on some easily-accessible removable medium, like a USB flash drive. If the partition table itself gets trashed in the future, you can then restore the original pretty easily.

Of course, disk problems can also affect the filesystems inside partitions, so backing up your actual data is also important. This is a bigger task, and there are a lot of different options for how to do it (both software and hardware). Lately I've been using a 1 TB external hard drive to back up several different physical computers. An ideal solution would involve multiple media, though, so that if the backup fails there'll be a backup for *it*, too. Tapes used to be very good for this, but they've fallen behind in terms of price and capacity.

As to your swap space, a reference to /dev/mapper suggests something in an LVM or motherboard-based software RAID (aka "fake RAID") setup. The name suggests something involving encryption, although my knowledge of Linux disk encryption is limited, so I don't know if these techniques also place device files in /dev/mapper. Have you ever used LVM, RAID, or encryption on this disk? If so, it's conceivable that your system is or was seeing old data associated with these technologies and so is trying to access your swap space in this way. (In fact, it's conceivable that old data of this sort confused GParted and caused this mess in the first place.)

If there's a real /dev/mapper/cryptswap1 file on your system right now, I recommend you track it down and figure out what it is before proceeding. If that file doesn't exist, it's probably safe to rewrite the /etc/fstab swap entry to access the swap partition by device filename or UUID.

---

### Post by Strigoides on 2011-05-17
I am using encryption, I selected the option to encrypt my /home partition on install of Ubuntu 11.04
As far as I can tell, /dev/mapper/cryptswap1 is a mapped device, which encrypts/decrypts data to/from the source device specified in /etc/crypttab:
```

# <target name>    <source device>        <key file>    <options>
cryptswap1 /dev/sda5 /dev/urandom swap,cipher=aes-cbc-essiv:sha256

```So, I will try changing the source device to /dev/sda6

---

### Post by srs5694 on 2011-05-17
No, if the system is encrypting your swap space and everything seems to be working, you should leave /etc/fstab alone, at least unless you hear otherwise from somebody who knows better than I on this topic. I've never used encryption, so I can't say what's normal for a system that uses encryption; however, it's plausible that swap space would be encrypted to keep data stored in memory and then swapped to disk from falling into the wrong hands.

---

### Post by Strigoides on 2011-05-17
I am leaving my fstab alone, I changed the source device in /etc/crypttab

---

### Post by srs5694 on 2011-05-17
Ah, OK, I misunderstood your comment.

---

### Post by catcatcher on 2012-01-16
[FONT=Calibri][SIZE=3]Create the partitions [provide inputs in terms of sectors and megabytes] as mentioned in below table using 2TB HDD.[/SIZE][/FONT]
[FONT=Calibri][SIZE=3] [/SIZE][/FONT]
[FONT=Calibri]Partition Number[/FONT]
[FONT=Calibri]Size of partition [units  in terms of sectors and megabytes][/FONT]
[FONT=Calibri]1[/FONT]
[FONT=Calibri]0 [Empty][/FONT]
[FONT=Calibri]2[/FONT]
[FONT=Calibri]50[/FONT]
[FONT=Calibri]3[/FONT]
[FONT=Calibri]0 [Empty][/FONT]
[FONT=Calibri]4[/FONT]
[FONT=Calibri]? [Find out the size?][/FONT]
[FONT=Calibri]5[/FONT]
[FONT=Calibri]200[/FONT]
[FONT=Calibri]6[/FONT]
[FONT=Calibri]300[/FONT]
[FONT=Calibri]7[/FONT]
[FONT=Calibri]150[/FONT]
[FONT=Calibri]Leave some gap, do not create any partitions here. The gap should be large enough, such that following partitions must be created at the end of the disk.[/FONT]
[FONT=Calibri]8[/FONT]
[FONT=Calibri]200[/FONT]
[FONT=Calibri]9[/FONT]
[FONT=Calibri]100[/FONT]

 
 
 
 
 
 
 
 
 
 
 
 
 
plz help or i wil lose my job..i am not able to do"
[FONT=Calibri]Leave some gap, do not create any partitions here. The gap should be large enough, such that following partitions must be created at the end of the disk.[/FONT]
"....i am using sfdisk command:confused:

---

### Post by catcatcher on 2012-01-16
[FONT=Calibri]how to leave gap between two partition...like gap between 1and 2 so ..gap should be so large that 1 os at the begining of 2TB HDD and partition 2 is at the ending of the hdd:popcorn:[/FONT]

---

