---
title: "Back up MBR"
date: 2010-04-21
forum: General Help
---

### Post by tjoshea13 on 2010-04-21
Just like the title says, I would like to be able to back up my MBR setup.
Is this possible and how would I go about doing it?

---

### Post by drs305 on 2010-04-21
You can run the following commands to backup/restore a drive's MBR. The value **512** includes the partition table information; change the value to **446** to back up the MBR without the partition table. Change the path/filename as desired.

Save:  
```
sudo dd if=/dev/**sda** of=/<path_to_file>/mbr.**512**.img bs=**512** count=1

```
Restore: 
```
sudo dd of=/dev/**sda** if=/<path_to_file>/mbr.**512**.img bs=**512** count=1
```

Of course you need to be careful any time you are restoring information to the MBR (correct command, destination, etc).

---

### Post by klemes on 2010-04-21
I think it goes like this:

sudo dd if=/dev/sda of=~/mbr.img bs=512 count=1

EDIT:Second again...;)

---

### Post by tjoshea13 on 2010-04-21
This will be within the terminal right?
 
and I can change the destination to an external drive?
 
Thanks for all your help

---

### Post by drs305 on 2010-04-21
> **tjoshea13 said:**
> This will be within the terminal right?
 
and I can change the destination to an external drive?
 
Thanks for all your help

Yes, you can change the path and filename to anything you want - the output is just a file. I add the numeral in my filename just to remember which one I recorded, but that isn't necessary. And use "sudo" in the command as was mentioned if you aren't 'root' or you will get a "Permission denied" message.

---

### Post by srs5694 on 2010-04-21
What is your specific goal in backing up the MBR? Do you want to have your boot loader in an easy-to-recover form, have your partitions in an easy-to-recover form, or both? I ask because the best way to do it depends on your goals.

The dd command, as others have suggested, backs up your boot loader and your primary partitions, but this will only restore your logical partitions if their own data structures (which are scattered through the extended partition) are themselves intact. To back up the partition table, including both the primary and logical partitions, it's better to use sfdisk:

```

sudo sfdisk -d /dev/sda > backup.txt

```

To restore this backup, you'd use:

```

sudo sfdisk /dev/sda < backup.txt

```

You might need to add the "-f" parameter right after sfdisk, depending on whether your backed-up partitions match sfdisk's standards of perfection.

If you *only* want to back up the boot loader, change the "bs" option in the dd commands others have recommended to "446". This will back up the boot loader *without* backing up the partition table. The result will be that you'll be able to restore the backup without affecting the partition table, which might be necessary in some situations. (If you've got a full 512-byte MBR backup and want to restore the boot loader alone, you can use "bs=446 count=1" on the dd restore command.)

Of course, there's nothing wrong with keeping two sets of backups -- one from dd and one from sfdisk. There is, though, a risk when using either tool: Certain typos can end up wiping out your partition table rather than backing it up! So be *very careful* with both dd and sfdisk!

One more comment: If you're using the GUID Partition Table (GPT) rather than MBR, neither of these backup methods will work. You can back up the primary (but not the backup) GPT data by using dd but extending it out to 34 sectors ("count=34" rather than "count=1"); however, if you restore this, the result won't be a complete GPT, since it will be missing the backup structures, which are stored at the end of the disk. Also, it's possible for GPT to use something other than the common 128-entry partition table size, in which case you'd need to back up something other than 34 sectors. OSes and utilities might or might not be happy with the result when you restore just the main partition table. An alternative is to use my [GPT fdisk](http://www.rodsbooks.com/gdisk/) to make a backup, using its 'b' main-menu option. This (or a dd-created backup) can then be restored using the 'l' option on the recovery & transformation menu. This restores both the main and backup data on the disk from the backup file. A GPT backup made in this way backs up both the partition table data and the boot loader.

---

### Post by Mike_tn on 2010-11-18
Im a little worried about trying this MBR backup, especially after warned about malicious block device manipulation by forums admin [[COLOR=#980101]**jdong**[/COLOR]]("http://ubuntuforums.org/member.php?u=780") here:

> **ATTENTION ALL USERS: Malicious Commands**
Block device manipulation: Causes raw data to be written to a block  device. Often times this will clobber the filesystem and cause total  loss of data:
 	Code:

 	dd if=something of=/dev/sda

Soooo is your code in proper conformity with that warning (not doing that)?

Maybe I don't even need MBR backup?  
Would reinstalling GRUB have the same effect and ease for most users?

In my system I dual install, first Windows 7 then Ubuntu and leave it alone.  Maybe tweak the seconds it sits at the boot screen via a Startup  Manager but that's no big deal to set up. So as an alternate MBR rescue to the "dd command backup", maybe this: wipe the MBR with a Windows rescue disk, install Windows boot system  with their rescue disk and then reinstall GRUB so Linux appears first in the boot order and you get the GRUB boot options on the first screen. 

But is there a reason to  use an MBR backup save-restore system instead of what I just mentioned?  Is it harder on the "life" your 1st partition to do one instead of the  other? Other reasons?

---

### Post by srs5694 on 2010-11-19
Mike_tn, I asked a question in my previous post that's extremely relevant:

[quote=srs5694]What is your specific goal in backing up the MBR? Do you want to have your boot loader in an easy-to-recover form, have your partitions in an easy-to-recover form, or both? I ask because the best way to do it depends on your goals.
[/quote]

In fact, please re-read that entire post, since it answers many of your questions.

The dd command is a general-purpose data copying command. Its if= and of= options specify the input file and output file, respectively, and this determines whether it could do anything malicious. The command presented by klemes backs up from the MBR of /dev/sda to a file, so it can't possibly be malicious or dangerous *unless* you goof and mix up the if= and of= options, in which case you could wipe out your boot loader and partitions.

As to whether you *need* a backup of your MBR, I'd say that it's not strictly necessary but is a good idea to have. A backup of the MBR *will* save you a lot of time and hassle if and when you accidentally wipe out your partitions. There are lots of posts here from people who've done just that. Usually they end up posting frenzied requests for help because they've just lost not just their OS but their family photos, music collection, etc. With a partition table backup on a USB stick, restoring partitions becomes a snap. Without that, you'll have to resort to TestDisk, or perhaps even guess. Although restoring that way can work, it's more hit-or-miss.

More broadly, most people don't pay sufficient attention to backups. It's best to get an external disk or even a tape drive or a stack of DVD+/-Rs and back everything up from time to time.

---

### Post by Herman on 2010-11-19
:D Hello all, can I chime in?

> What is your specific goal in backing up the MBR? Do you want to have  your boot loader in an easy-to-recover form, have your partitions in an  easy-to-recover form, or both? Nowadays more people have some understanding about what a MBR is and what it is made up of. We have easy to use software for working on the MBR, the use of the dd command to back up the MBR seems less important for most of us.
If we're Linux-only users, or if we dual boot Windows XP or eariler, there's no need for a MBR backup now unless there's some specific reason for wanting one.
For a standard PC, it's generally easier to just re-install a boot loader or use TestDisk to recover a corrupted partition table, and if it wasn't for the existence of Windows Vista and Windows 7's BCD loader, nobody would probably care about making a dd backup of their MBR. 
For some reason though, (in their wisdom), Microsoft decided to make their BCD boot loader depend the MBR's 'Disk Identifier'. I don't know why, possibly something to do with anti piracy?

The hard disk's 'Disk Identifier' is unique to each hard disk and is vital for booting Windows Vista and Windows 7.

It means if you use TestDisk  or GParted to write an new MBR, or if your hard disk is about to fail and you need to copy your operating systems to a different hard disk drive you won't be able to boot Windows Vista or 7 again. (Or at least *I* don't know how, maybe Windows Tech support can help you).
A dd copy of the first 446 bytes of the old MBR, which includes the 'Disk Identifier' can save you a lot of trouble. You can copy the dd backup of the old MBR to the new one without affecting the partition table and then restore the boot loader, GRUB will preserve the MBR's 'Disk Identifier'.
```
Disk /dev/sdb: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
[COLOR=Red]**Disk identifier: 0x6f5f77f3**[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          63   625137344   312568641    7  HPFS/NTFS
```Regards, Herman :)

---

### Post by Mike_tn on 2010-11-20
> **srs5694 said:**
> 
In fact, please re-read that entire post, since it answers many of your questions.
thanks, sometimes I'm a careless reader, I did reread it.

> **srs5694 said:**
> The command presented by klemes backs up from the MBR of /dev/sda to a file, so it can't possibly be malicious or dangerous *unless* you goofgood to know you concur on the code up there, thanks

> **srs5694 said:**
> As to whether you *need* a backup of your MBR, I'd say that it's not strictly necessary but is a good idea to have. A backup of the MBR *will* save you a lot of time and hassle if and when you accidentally wipe out your partitions.It happened twice, MBR meltdown.

**1st time** before my current full install I had added Ubuntu Lucid to Windows as Wubi, finally got online after a wireless driver fix, ran the update manager, Grub2 now called just Grub was updated and it was bye bye MBR. Caught me off guard. I was unfamiliar with MBR reinstalls except some of my Acronis software had system state backup, I hadn't kept up with that, so I do it (did it) by restoring Windows entirely from the most recent full system image backup.  Then reinstalled Grub with EasyBCD which I don't use now. So I got my access & MBR back that way but the full image backup is usually dated by a week or month, minimum. That could be annoying to get up to speed, and in that case it was!

**2nd time** the MBR died was an interesting phenomenon. I had put Ubuntu on my laptop and Mandriva Linux as a full normal install (not Live) onto an 8GB USB plugged into an offline desktop PC, this machine now also dual booted but with XP and the USB Linux install.  Well I discovered a Live USB operates differently than full installs when I tried booting that stick in my Ubuntu/Windows7 laptop. Something happened, maybe because the Mandriva install on a USB had an older version of Grub.  The laptop's MBR was mangled again. DOH! My advice: put only Live OS on your USB! This time I fixed it the same way, full system image restore but hadn't been using Windows at all so it didn't matter how old my image was.

> **srs5694 said:**
> More broadly, most people don't pay sufficient attention to backups.  It's best to get an external disk or even a tape drive or a stack of  DVD+/-Rs and back everything up from time to time.Since that time I learned how to use system repair disks & live disks to put the MBR back. But I'm not sure my methods will work in every situation.  When you can't get into the OS and have to work in the recovery environment, it gets strange, at least with dual booting. Seems a copy of the MBR that can be put back with the command line would be a good time saver. I always backup my data, continuously, do it by hand but also started to use "sbackup", simple backup tool in the repository. Even if we can get everything back by reinstalling the OS, I'd like it to be as quick as possible. If the only issue is the MBR, I'd much rather be able to fix that and be done.

I suppose I should use both sfdisk and dd. Seems one should cover it all though. I'll probably have to use them to really understand them and my need.

MBR work conjurs up thoughts of advertisements from the movie Tron. My body may become digitized and my next post will be from the inside.

> **Herman said:**
> 
if it wasn't for the existence of Windows Vista and Windows 7's BCD  loader, nobody would probably care about making a dd backup of their  MBR. 
For some reason though, (in their wisdom), Microsoft decided to make  their BCD boot loader depend the MBR's 'Disk Identifier'. I don't know  why, possibly something to do with anti piracy?

The hard disk's 'Disk Identifier' is unique to each hard disk and is vital for booting Windows Vista and Windows 7.

A dd copy of the first 446 bytes of the old MBR, which includes the 'Disk Identifier' can save you a lot of trouble.

Thanks! I'll take that as a vote for leaning the MBR backup method.

And I have another motivation to not care if one day I say goodbye to Windows entirely. That company, in trying to prevent piracy only drives more people like me toward using Linux alone.

---

### Post by Mike_tn on 2010-12-04
> 
The dd command, as others have suggested, backs up your boot loader and your primary partitions, but this will only restore your logical partitions if their own data structures (which are scattered through the extended partition) are themselves intact. To back up the partition table, including both the primary and logical partitions, it's better to use sfdisk:

```

sudo sfdisk -d /dev/sda > backup.txt

```***

I ran all 3 sets, 
dd at 512, dd at 446, and sfdisk.

A couple concerns on the file outputs:

For both dd img created files, the file belongs to root.  Do I need to edit the permissions before it can be used in a restore situation?

For sfdisk I got a warning, presumably because I am using a Ubuntu-Windows dual boot and left the manufacturers original Windows first partion intact.  Which is about 50GB for the Windows 7 OS and then made an extended partition out of the rest like this>

**|**W7-Primary**|**Data-Logical**|**Ubuntu**|**Swap**|**

In the terminal output it said[INDENT][B]Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

[/B][/INDENT]I recall reading about this cylinder boundry issue when I installed my first Ubuntu and so making the data partition space inbetween the two operating systems keeps everything happy, if I recall right.  Is this warning a problem in a typical restore situation using fsdisk?
The saved filed looked like this except I added the (Titles) on their left side, from memory, pretty sure they are right.[INDENT]# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=     2048, size=   204800, Id=de, bootable
/dev/sda2 : start=   206848, size= 20480000, Id= 7     (Recovery)
/dev/sda3 : start= 20686848, size=122880000, Id= 7  (W7)
/dev/sda4 : start=143572990, size=481568770, Id= f  (Extend)
/dev/sda5 : start=143575040, size=225464320, Id= 7  (Data)
/dev/sda6 : start=499226624, size=120686592, Id=83 (Ubuntu)
/dev/sda7 : start=619915264, size=  5226496, Id=82   (Swap)
[/INDENT]

---

### Post by srs5694 on 2010-12-04
> **Mike_tn said:**
> I ran all 3 sets, 
dd at 512, dd at 446, and sfdisk.

A couple concerns on the file outputs:

For both dd img created files, the file belongs to root.  Do I need to edit the permissions before it can be used in a restore situation?

No; you've got to be root to restore the backup anyhow, so this is fine. (Using "sudo" makes you root for that one command, in case you didn't know this.)

> For sfdisk I got a warning, presumably because I am using a Ubuntu-Windows dual boot and left the manufacturers original Windows first partion intact.  Which is about 50GB for the Windows 7 OS and then made an extended partition out of the rest like this>

**|**W7-Primary**|**Data-Logical**|**Ubuntu**|**Swap**|**

In the terminal output it said[INDENT][B]Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.

[/B][/INDENT]

Don't worry about it. Partition alignment standards are changing from the truly ancient cylinder-boundary alignment to 1 MiB alignment. Only ridiculously old OSes, such as very old versions of DOS, have problems with the newer 1 MiB alignment. Unfortunately, a lot of utilities are still fussy about it or can get confused when they try to apply one set of alignment rules to a disk that was partitioned using another set of rules. At worst, you'll need to use the "-f" ("--force") option to sfdisk when restoring the partitions you've backed up.

---

### Post by Mike_tn on 2010-12-04
> **srs5694 said:**
> No; you've got to be root to restore the backup anyhow, so this is fine.
***
Don't worry about it. ... At worst, you'll need to use the "-f" ("--force") option to sfdisk when restoring the partitions you've backed up.

Ahhh, thank you for your input here. This thread has been a blessing.

---

