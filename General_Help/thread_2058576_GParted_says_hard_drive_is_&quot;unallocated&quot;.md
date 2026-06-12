---
title: "GParted says hard drive is &quot;unallocated&quot;"
date: 2012-09-16
forum: General Help
---

### Post by Cipher1874 on 2012-09-16
I'm attempting to back up the files on my hard drive, because my laptop seems to have crashed after a failed update, and only sent me to the recovery console. I'm on Xubuntu now, but the hard drive seems to be acting up. (also, on a side note, the recovery console and the option to boot from my hard drive and the option to add a new boot option) disappeared at some point,  though the last one appears when I plug in a usb. :confused:

Anyway, this is what sudo fdisk -l says:

> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
256 heads, 63 sectors/track, 60563 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2902cc6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1  4294967295  2147483647+  ee  GPT

Disk /dev/sdb: 15.7 GB, 15703474176 bytes
256 heads, 54 sectors/track, 2218 cylinders, total 30670848 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32    30670847    15335408    c  W95 FAT32 (LBA)

I was trying to follow Enigmapond's post in this thread: [http://ubuntuforums.org/showthread.php?t=1841546](http://ubuntuforums.org/showthread.php?t=1841546)

But I can't mount the partition into the folder, because I must "specify the filesystem type."
Help would be greatly appreciated. I'm not much of a tech person, and my laptop is just baffling me to no end with these issues.  /:

---

### Post by Bucky Ball on 2012-09-16
Can you get to a desktop okay? Launch Gparted and have a look at what that says. 

The Windows partition doesn't appear in the left pane of the file browser normally? The instructions on that thread seem okay. You should though do mount it in an existing partition designed for that, /mnt or /media.

```
sudo mkdir /media/win
sudo mount /dev/sda1 /media/win
```... presuming sda1 is the partition you have Win on. 

You can change the /etc/fstab file to mount it at boot which save a lot of hassle.

---

### Post by Cipher1874 on 2012-09-16
No, the Windows partition doesn't pop up. Though it seems that the operating system was corrupted and is now missing, so could that be why?
This is what it shows:
[IMG]http://i45.tinypic.com/42df6.png[/IMG]
I tried that, but it still says that I have to specify the filesystem type.

What's the /etc/fstab file and what would changing it do? Sorry, I've never dealt with like any of this stuff before.

---

### Post by JKyleOKC on 2012-09-16
That first line from fdisk says it all: > WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.You probably have a machine that uses the newer UEFI boot system, which means that most of the advice you can find on the web will not only be wrong for your system but can easily make matters much worse.

You can find more than you probably want to know right now about this new system, at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) but it's not going to solve the immediate problem.

Were it my machine involved, I would follow the advice given by the Gparted popup message -- but since that just might wipe the machine totally clean and make recovery impossible, I can't recommend it to you. Hopefully one of the few UEFI experts around will find this thread and offer better ideas. I've sent messages to a couple of them asking them to stop by. Meanwhile, don't do anything that might make matters worse than they already are...

---

### Post by Cipher1874 on 2012-09-16
Alright, thank you very much. I guess that makes sense. I'll just wait before doing anything else, in that case.

---

### Post by oldfred on 2012-09-16
Is your system new? And have UEFI? Windows only works on gpt partitioned drives with UEFI, otherwise it should be MBR(msdos) partitioning. 

Windows often deletes the primary gpt table if found as gpt and installs to MBR. But Linux tools still see the backup gpt table and get confused if gpt or MBR and do not do anything.

Your gparted is saying both primary & backup gpt tables are bad which is highly unusual. Or maybe it is not really gpt?

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

You can also try testdisk, but may have to go into it from both the MBR and gpt modes to see which mode will recover an old partition table.

repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
[http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS](http://www.cgsecurity.org/wiki/TestDisk:_undelete_file_for_NTFS)

From this screen in testdisk try both Intel for MBR(msdos( and UEFI gpt for gpt(GUID) partitioning. See if either shows any partitions.

---

### Post by JKyleOKC on 2012-09-16
Thanks for responding so quickly, Fred!

---

### Post by Cipher1874 on 2012-09-16
It's new, yes. I got it in late May. I don't know if it has UEFI, how do I find that out?

I'll try to repair GPT first. How do I access gdisk?
Also, why does the size show up as 465GB when the hard drive is 500GB?
And thank you, that was a very fast answer indeed.

---

### Post by oldfred on 2012-09-16
gdisk is in the repository, so from Ubuntu liveCD terminal you can just run this.

sudo apt-get install gdisk

#similarly for testdisk

sudo apt-get testdisk

When you go into BIOS/UEFI it should say or show UEFI as a switch you can turn on. Some only defaulted to UEFI boot if drive was gpt and first partition the efi partition, if not found then it would boot in BIOS/MBR mode. Newer systems seem to have a setting for UEFI or BIOS/AHCI/legacy or whatever your version calls it. Also vendor manual should mention UEFI.

Most Intel i series chips have motherboards with UEFI capability.

Drive size seems about right. The issue is decimal vs. binary.
Hard Drive size
[http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion](http://en.wikipedia.org/wiki/Gigabyte#Consumer_confusion)

---

### Post by Cipher1874 on 2012-09-16
The first one works, however when I try to do the same for testdisk it says:
E: Invalid operation testdisk

---

### Post by oldfred on 2012-09-16
Left off the install

sudo apt-get install testdisk

---

### Post by Cipher1874 on 2012-09-16
Alright, that's done. So now I turn off my laptop and go into BIOS to check if it's UEFI?

Also, I went ahead and tried the backup process in the link for repairing GPT, but when I typed in **sgdisk -b sda-backup.gpt /dev/sda**, I get the following message: Problem [B]opening /dev/sda for reading! Error is 13.
You must run this program as root or use sudo![/B]

---

### Post by oldfred on 2012-09-16
If you are booting liveCD or USB, the programs you just installed will not be saved. You have to reinstall each time you boot CD as CD is not writeable. You can change some settings on USB flash installer to save some data with a  persistent setting.

I do not know what error 13 is. Try with sudo. But if gparted said table was bad then even gdisk may also see the errors and have problems trying to back up damaged data.

What does testdisk show?

---

### Post by Cipher1874 on 2012-09-16
> xubuntu@xubuntu:~$ sudo sgdisk -b sda-backup.gpt /dev/sda
Caution! After loading partitions, the CRC doesn't check out!
Warning! One or more CRCs don't match. You should repair the disk!

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
The operation has completed successfully.

How do I open testdisk? Sudo? So it'd just be **sudo testdisk**?

---

### Post by oldfred on 2012-09-16
Yes sudo testdisk should work?

How did partitions get changed? Did you run some utility or installer somewhere?

---

### Post by Cipher1874 on 2012-09-16
Alright, I'll run that right now. It shows:
> TestDisk 6.13, Data Recovery Utility, November 2011
Christophe GRENIER <grenier@cgsecurity.org>
[http://www.cgsecurity.org](http://www.cgsecurity.org)


TestDisk is free data recovery software designed to help recover lost
partitions and/or make non-booting disks bootable again when these symptoms
are caused by faulty software, certain types of viruses or human error.
It can also be used to repair some filesystem errors.

Information gathered during TestDisk use can be recorded for later
review. If you choose to create the text file, testdisk.log , it
will contain TestDisk options, technical information and various
outputs; including any folder/file names TestDisk was used to find and
list onscreen.

Use arrow keys to select, then press Enter key:
>[ Create ] Create a new log file
 [ Append ] Append information to log file
 [ No Log ] Don't record anything
Do I select create or append?

And no, I don't really know anything about that, so I have no idea how to change partitions.

---

### Post by oldfred on 2012-09-16
Log file is in case you want to know what happened. Not sure if it offers anything else or not. I usually check no log file.

---

### Post by Cipher1874 on 2012-09-16
Alright, I clicked intel / pc and then I click analyse?

When I do, it says this:
> Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P EFI GPT                  0   0  2 267349  89  4 4294967295

Warning: Bad ending head (CHS and LBA don't match)
No partition is bootable

---

### Post by oldfred on 2012-09-16
It also is seeing it as gpt. Try the gpt or second entry.

---

### Post by Cipher1874 on 2012-09-16
You mean this link, right?
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

The problem is, I still can't back it up using the command given in bold.

---

### Post by oldfred on 2012-09-16
that is because it is so damaged.

From testdisk and efi/gpt what did it show?

Again what did you do to get to this point. It might help in trying to solve the issue.

And what is in the partition?

---

### Post by Cipher1874 on 2012-09-16
Testdisk shows this:
> xubuntu@xubuntu:~$ sudo sgdisk -b sda-backup.gpt /dev/sda
Caution! After loading partitions, the CRC doesn't check out!
Warning! One or more CRCs don't match. You should repair the disk!

**************************************************  **************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
**************************************************  **************************

Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
The operation has completed successfully.

The only point at which I noticed that it started to have more problems was after I tried updating the BIOS by putting the newest version on the flash drive and then installing that using EasyFlash. After that, the option to boot from the hard drive was gone, along with the option to add a new boot option, until I plugged in my USB or entered a CD.

That partition is my laptop's internal hard drive.

Is that all the information that you wanted? If there's anything else just let me know, though I might need help figuring out how to go about getting it.

---

### Post by Cipher1874 on 2012-09-16
Also, for more information, the BIOS was downloaded directly from the ASUS site (this was the most recent for the R500VD model) and it was this version:
                 Version                  404                             
                                       
                                 Description                               BIOS 404
1.Fix the issue that SecureBoot will be disabled if BIOS is updated by EzFlash or WinFlash                                         File Size                                                                                              2,69 (MBytes)                                                                   2012.09.06                          update                                                                                            Download from                                                                                                [IMG]http://support.asus.com/images/asus_download_pics01.gif[/IMG] Global (DLM)                           [IMG]http://support.asus.com/images/asus_download_pics02.gif[/IMG] Global

---

### Post by oldfred on 2012-09-16
Well,  secure boot is the new issue with Windows 8 and UEFI systems. That locks system and only Windows will boot. I did not think any vendor has turned on the secure boot flag yet, but it is a requirement with all new Windows 8 systems.

You posted the info from gdisk or sgdisk as it is always suggested to backup partition table before making changes.

Did you try testdisk and the efi/gpt and deeper search?

---

### Post by Cipher1874 on 2012-09-17
Okay, so you don't think that it could have anything to do with the BIOS update using EasyFlash? Because after that is when the recovery console went away and I could no longer boot from the hard drive. Just making sure that I didn't do something that might have damaged the hard drive by doing that.

Well, testdisk said this:
> Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P EFI GPT                  0   0  2 267349  89  4 4294967295

Warning: Bad ending head (CHS and LBA don't match)
No partition is bootable 			 		
Which of the links you sent me is the one that you're suggesting me to use?

---

### Post by oldfred on 2012-09-17
Well, it does not matter as neither is working.

Not sure how but we need to shrink the partition slightly so the sgdisk is not complaining about overlap. I have not done that from gdisk, only from gparted. But because of the errors gparted will not work for you.

Can you skip the backup and try gdisk and several of its commands. I expect it may not work either, but we need to try.

first (not sure if sudo required from liveCD?)
gdisk /dev/sda

Without know exact errors I cannot suggest, but gdisk page has several suggestions on commands to use.

---

### Post by Cipher1874 on 2012-09-17
I had to use sudo for it, and it said this:
> xubuntu@xubuntu:~$ sudo gdisk /dev/sda
GPT fdisk (gdisk) version 0.8.1

Caution! After loading partitions, the CRC doesn't check out!
Warning! One or more CRCs don't match. You should repair the disk!

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: damaged

****************************************************************************
Caution: Found protective or hybrid MBR and corrupt GPT. Using GPT, but disk
verification and recovery are STRONGLY recommended.
****************************************************************************

Warning! Secondary partition table overlaps the last partition by
33 blocks!
You will need to delete this partition or resize it in another utility.
It's very similar to what's shown in the link you gave me, but I'm not sure what to do after that, since after it seems to cut to a different section about manual recovery.

---

### Post by oldfred on 2012-09-17
Nothing seems to want to open partitions so you can resize it and as long as it overlaps, gdisk will not even let you do anything. Do you have any details on what the partition table structure was? How many partitions and sizes?

Do you have data you want to attempt to recover.

Testdisk has photorec which just scans drive for anything that looks like a file by types. It does not recover filename, just extension. Some files like music & photos do have internal data that can be used to rename to a better name. Process is very long (I have used it) and you need another drive with enough room to copy all your data to.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

Then just totally erase & reformat drive.

---

### Post by Cipher1874 on 2012-09-17
How do I check the partition, again? Is that fdisk?
 
 Yes, I do. Will I have to run it once for each file type, or is there a  way for me to just enter multiple file types? Around how long would the  process be for a 500GB hard drive?
 The files I'm trying to recover are pictures and videos that I had  placed on my laptop to have space on my camera's SD card, which I  foolishly didn't think to back up elsewhere. 
 
 Alright, I'll only need something with enough space to hold the pictures  / videos that it finds? If so, I have a 16GB flash drive that should do  the trick, the SD cards I moved onto here were 1GB and 4GB cards, and  other than that, my laptop doesn't have much at all on it since it's  pretty new.

Also, do you know if picture info (like when it was created) will still show up?
Thank you, I'll begin reading the information in the links now.

---

### Post by oldfred on 2012-09-18
Try testdisk one more time and try deeper search if it will let you. If deeper search works then it finds file names. But even deeper search takes a long time.

If you  have a 500GB drive it will be at least over night for photorec. I think it was about 6 hours and I was only trying to recover two folders. But I think it searched entire drive and found many files. Your 16GB flash will not be enough. For me I have saved some text files many, many times. Since the deleted files were still there it recovered all the deleted one's also. I was never sure I recovered the last saved version. 

There is a menu setting on extensions to search for. But it does not speed it up as it still scans every bit on disk and trys to find what looks like a file start, file end and then write that file. You may save the bit of time writing files you may not want. 

The larger the file the less chance it will recover it correctly. Pictures should be ok, but you will just have to see what it can find.

---

### Post by Cipher1874 on 2012-09-18
Would deeper search be able to find a folder, or just specific files? If so, that might be harder than Photorec for me.

---

### Post by oldfred on 2012-09-18
Testdisk will find folders with the full file name if deeper search works. 

Photorec only finds file extensions and may find previously deleted files also.

---

### Post by Cipher1874 on 2012-09-18
That's great, thank you! I'll have to buy an external hard drive, so I'll try that ASAP and then let you know. It sounds promising. I hope deeper search works.

---

### Post by Cipher1874 on 2012-10-06
Alrighty! Time for some results, now that I've got the external hard drive.

Trying testdisk (analyse) for Intel, results:
> Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 P EFI GPT                  0   0  2 267349  89  4 4294967295

Warning: Bad ending head (CHS and LBA don't match)
No partition is bootable

Testdisk for UEFI:
> Disk /dev/sda - 500 GB / 465 GiB - CHS 60801 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

Bad GPT partition entries, invalid checksum.

Photorec for sda shows me this:
> Disk /dev/sda - 500 GB / 465 GiB (RO) - ST9500325AS

     Partition                  Start        End    Size in sectors
      No partition             0   0  1 60801  80 63  976773168 [Whole disk]
> 1 P EFI GPT                  0   0  2 267349  89  4 4294967295
I'm guessing that I go with 1 P EFI GPT?

Which shows this:
> Please select a destination to save the recovered files.
Do not choose to write the files to the same partition they were stored on.
Keys: Arrow keys to select another directory
      C when the destination is correct
      Q to quit
Directory /home/xubuntu
>drwxr-xr-x   999   999       680  7-Oct-2012 01:55 .
 drwxr-xr-x     0     0        60  6-Oct-2012 21:26 ..
 drwxr-xr-x   999   999        60  6-Oct-2012 21:26 Desktop
 drwxr-xr-x   999   999        40  6-Oct-2012 21:28 Documents
 drwxr-xr-x   999   999        40  6-Oct-2012 21:28 Downloads
 drwxr-xr-x   999   999        40  6-Oct-2012 21:28 Music
 drwxr-xr-x   999   999        40  6-Oct-2012 21:28 Pictures
 drwxr-xr-x   999   999        40  6-Oct-2012 21:28 Public
 drwxr-xr-x   999   999        40  6-Oct-2012 21:28 Templates
 drwxr-xr-x   999   999        40  6-Oct-2012 21:28 Videos
 -rw-r--r--     0     0     40960  7-Oct-2012 01:55 photorec.ses
How do I designate it to save to my external hard drive? Is it one of the first two options?

---

### Post by oldfred on 2012-10-08
Did you mount the other directory? I do not know if xbuntu, but if you click on a folder in the file browser it will mount it.

You did create partition(s) and format them on the new drive?

---

### Post by Cipher1874 on 2012-10-10
I actually don't really know what that means. Mount which other directory?
Do you mean like I did before with sudo mount /dev/sda?

And create new partitions on the external hard drive? No, how do I do that?

---

### Post by oldfred on 2012-10-10
Depending on what type of drive you purchased, it probably is not partitioned nor formated. If an external drive it may be formated FAT32 which you do not want.

gparted & fdisk instructions:
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)
Partitioning basics with some info on /data, older but still good bodhi.zazen
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

---

### Post by Cipher1874 on 2012-10-10
Can I format it on another computer?
And it says on the website that if it's to be used between Ubuntu and Windows, it should be formatted FAT32. If I'm using an ext3 system, how will I later use my new external hard drive on a computer running windows? 

So after I've formatted it, I should be able to find it with Photorec in order to copy the files onto it?

---

### Post by Bucky Ball on 2012-10-10
NTFS, *not* FAT32. You must be looking at a very old website or its author had some reason for using FAT32.

NTFS is preferable and readable between the two (Win installs on NTFS). Win won't read EXT* so a shared partition between the two is the easiest.

---

### Post by oldfred on 2012-10-10
If you are backing up system then it should be LInux for permissions & ownership. 

But if sharing with Windows only data NTFS is much preferred over FAT32. FAT32 has  a limit of 4GB files and does not have a journel, so issues take longer to fix or may not be fixable with chkdsk.

---

### Post by Cipher1874 on 2012-10-15
Alrighty. Testdisk one last time on the hard drive (/dev/sda)  under Intel, I selected analyse 
and then selected quick search, to which it gave me this:
"Should Testdisk search for partition created under Vista or later? (y/n)"
To which I selected yes, and then it found something (I think it autoselected it, because I don't think I hit enter) and now it's doing a deepersearch which has so far has found:
>   FAT32                    0  32 33    25 159  6     409600 [SYSTEM]
  FAT32                    0  32 33    25 159  6     409600 [NO NAME]
  HPFS - NTFS             41 240  8 24362 119 13  390709248 [OS]


Am I on the right track?

---

### Post by oldfred on 2012-10-15
Looks that way.

The first two are just versions or slight changes to the first FAT partition and then it shows a second NTFS partition. In fact start & end are identical on FAT and name seems to be only difference. Did you at some time change labels or maybe that was done before  you purchased system?

---

### Post by Cipher1874 on 2012-10-15
I haven't changed labels, I actually have no idea how to do that.
It's got this now (at 64%)
> FAT32                    0  32 33    25 159  6     409600 [SYSTEM]
  FAT32                    0  32 33    25 159  6     409600 [NO NAME]
  HPFS - NTFS             41 240  8 24362 119 13  390709248 [OS]
  HPFS - NTFS          24362 119 14 57614  99 21  534192128 [DATA]


Alright, update:
What do I do now? Select data? And just enter, none of the keys listed at the bottom?
[IMG]http://i50.tinypic.com/bdv4vs.png[/IMG]

---

### Post by oldfred on 2012-10-15
It says structure ok, just showing all partitions as deleted. I would change them back. May all primary for now, make the OS bootable.

---

### Post by Cipher1874 on 2012-10-15
Oh, okay, so the problem is that all the partitions were deleted? That just means that they were made inaccessible, but they still exist, right? 
How do I change them back, just hit "p" for each one to make it primary, and then I should be able to run it?
Edit: Alright, I can tell that "p" isn't it. How do I change them?

Edit 2: Oh, okay! It's right arrow. They're all primary now. Am I good to go? Can I get out of terminal and restart, and that should do the trick, or is there something else that I need to do beforehand?

---

### Post by Cipher1874 on 2012-10-15
Okay, I closed down terminal after making everything primary, I shut down the laptop and removed the CD and then turned it back on. I only get the message "Machine Check Error," and when ai out the CD in it won't do anything. I hit F2 and there's still no boot option for the hard drive. 

So... at this point it looks like it's completely unaccessible.

---

### Post by oldfred on 2012-10-15
I would be surprised if  Windows would boot after any major corruption. Does your gparted show the partitions now or what messages does it give.

Can xubuntu mount partitions.

Do you have Windows repairCD to run Windows repairs?

---

### Post by Cipher1874 on 2012-10-16
oldfred- No, nothing boots anymore at all.

I have a Windows 7 ISO. But I've tried it before, an it couldn't access the hard drive. This time it probably won't even open.

Terrymary512- None of the pictures show up for me.

---

### Post by oldfred on 2012-10-16
What does gparted say about drive?

---

### Post by Cipher1874 on 2012-10-16
How am I supposed to access gparted if I can't run the Ubuntu live CD (or anything, for that matter) anymore?

---

### Post by oldfred on 2012-10-16
Even if drive has issues you should be able to boot from CD or USB using BIOS or one time boot key (f12 on my system).

We have seen were some systems need a cold reboot, or full power down. If laptop remove battery for a couple of minutes. Then you should be able to use BIOS or one time boot key to choose CD or USB to boot from.

---

### Post by Cipher1874 on 2012-10-17
I just tried turning it back on, and it works from the CD! 
I'll be checking gparting and updating on what it shows in a second.

---

### Post by Cipher1874 on 2012-10-17
Ah, looks like it still goes back to the original issue:
[IMG]http://i46.tinypic.com/smwuph.png[/IMG]

---

### Post by oldfred on 2012-10-17
Do you have data you want to try to recover?

I might try testdisk once more and if not, then testdisk has photorec which scans drive for anything that looks like a file.

With testdisk are you using Intel or efi-gpt?

---

### Post by Cipher1874 on 2012-10-17
Yes, I do. Alright, so just testdisk, or photorec? How do I decide between the two? I think the one I tried was Intel. Whichever was first.

---

### Post by oldfred on 2012-10-17
Your first post said gpt? 

But sometimes gpt drives are mis-identified. Windows only installs to gpt drives with UEFI. And if installed to a drive with gpt it changes it to MBR if not in UEFI mode but does not erase the backup gpt partition table and Linux tools get confused if MBR or gpt as they see both.

Try both with testdisk. Sometime testdisk will see all the files & let you copy to another drive or flash drive. You then will get file names. 

If you cannot get that to work then you have to use photorec. But that is a long process, only recovers file extensions and you then have to manually sort thru and rename files. It also recovers any old deleted versions also. I had to use photorec once. It recovered some of my same text files many times. I had an older backup and many updates but was never able to tell which was the newest saved copy. I got most of data back but it took weeks - off and on. There are some scripts to help sort and music & photos have internal data to help recover useful filenames.

---

### Post by Cipher1874 on 2012-10-17
Alright, I mounted my external hard drive and by chance managed to find where I had mounted it to in the directory because that thing was like a maze for me. Anyway, it's saying that it's finding files and showing how many of each type!

---

### Post by Cipher1874 on 2012-10-17
It looks like it didn't have enough space, and it had just started. What do I do now?
Edit: Actually, it looks like I was saving the recovered files to the desktop's external folder within the media folder. I just had to go one step further to select the Seagate Expansion Pack External Hard Drive. Looks like everything is going smoothly, but wow. It's literally recovering every image the computer had on including stuff for programs. (Using photorec)

---

### Post by oldfred on 2012-10-17
If using photorec you do need lots of room. It recovers deleted copies also as it still is a file on drive. Deletion only removes entry in file table with file name, not data itself.

These may help a little on sorting files.

Use scripts to help sort and rename files:
[http://www.cgsecurity.org/wiki/After_Using_PhotoRec](http://www.cgsecurity.org/wiki/After_Using_PhotoRec)
use flac tags to rename files 
[http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html](http://lglinux.blogspot.com/2008/10/use-flac-tags-to-rename-files.html)
[http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/](http://system-tricks.com/index.php/datarecovery/sort-testdisk-photorec-data-recovery-results/)
Best GUI Indexing/Search Tool for Local Files? 
[http://ubuntuforums.org/showthread.php?t=1739701](http://ubuntuforums.org/showthread.php?t=1739701)

---

### Post by Cipher1874 on 2012-10-17
Would it be possible for me to just stop photorec right now and let the files that have been recovered stay recovered and then just let testdisk run? Or is this not advised? Ideally I'd just use testdisk, because I probably don't have the space for photorec's finds and don't need most of them.

---

### Post by oldfred on 2012-10-17
No idea. 

Generally I do not like stopping tasks, but on your drive it is just reading so it may be ok. I doubt that you can then restart where it is. It would just start all over. I think on my system it took over 6 hours for photorec. I really only lost a folder, but it seems to scan entire drive. There is an advanced setting in photorec to just recover certain types of files. It shows file extensions to try to recover. Not any faster as it still scans entire drive.

---

### Post by Cipher1874 on 2012-10-17
Alright, well, I stopped it for now. The amount of files was getting to be overwhelming, so hopefully testdisk's deeper search will work.
With that I should be able to search for a specific folder and then find that and its contents, correct?

Also, after the first run stopped because there wasn't enough space and I selected the correct directory, for some reason this one seems to have waaaay less image files than the first run. And most are thumbnails. I only managed to find 2 photos so far. And it looks like videos got converted to tiny .jpegs? Unless those are just the thumbnails, in which case I'm guessing that some of the many .avi files that I can't play are what I'm looking for.

So once the files are in the new location, are they removed from the hard disk?

---

### Post by oldfred on 2012-10-17
I do not think they are removed from hard drive. It is just finding things that look like files & copy to backup location. You may get thumbnails and all the other little support files.

---

### Post by Cipher1874 on 2012-10-17
For some reason the files from the first run weren't in the second (or at least not in the first few files of the second) so that's why I was asking.

I really hope testdisk works.

Also, how does that Python script for organizing the files by type work?

---

### Post by oldfred on 2012-10-17
I did not use any of those scripts, I did not know they existed until after I used photorec.

I wrote a one line command and manually updated it each time with every folder & file type. I knew I could convert it, but had not done much bash at the time and was only doing it once (I hoped).

---

### Post by Cipher1874 on 2012-10-17
Ah, okay. I guess I'll just sort through it all manually.

Testdisk shows all partitions as deleted again.

---

### Post by Cipher1874 on 2012-10-17
Also, I selected "Data" and it said that there was no partition to recover or something and then sent me back to the "analyse" option.

---

### Post by oldfred on 2012-10-17
Are you in MBR or gpt mode. I might try both.

If you undeleted before I do not understand why they are now deleted again, or did you not save the changes?

---

### Post by Cipher1874 on 2012-10-18
Okay, things are looking hopeful! Now that the partitions were undeleted, I went ahead and restarted, and now I can see the stuff from my other drive on there (somewhat, not sure if data can be accessed with that). So I went ahead and put in my Win7 ISO, and ran that, and then ran the startup repair which found and fixed a problem. Then it restarted and I tried startup repair again and this time it didn't find anything, though the laptop still can't boot that OS because I'm guessing parts are missing, but now I know I can re-install it pretty simply. 

So now how do I get to my files? Hopefully this means that this will be a lot easier than before! (:

---

### Post by Cipher1874 on 2012-10-18
xubuntu@xubuntu:~$ sudo fdisk -l

> WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2902cc6d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048      411647      204800    b  W95 FAT32
/dev/sda2   *      673792   391383039   195354624    7  HPFS/NTFS/exFAT
/dev/sda3       391383040   925575167   267096064    7  HPFS/NTFS/exFAT
/dev/sda4       925575168   976773167    25599000    7  HPFS/NTFS/exFATThough testdisk once again showed the partitions as deleted, strangely enough, even though the System, Data, OS, and Recovery sections are showing up on my desktop, so I changed them all back to primary. It says that no partition is bootable, though?

Running testdisk again with deeper search for both Intel and EFI/GPT. Also running GParted now with the recovery option.

Edit: And for MBR, since it rewrites itself into the hard disk, how do I go about changing that back if / after it works?

Edit two: I FOUND THE FILES! OS- > Users

---

### Post by oldfred on 2012-10-18
If you really have gpt and then Windows has to be in UEFI mode. And all gpt partitions are primary. 

Boot flag should then be on the efi partition, although in gpt/UEFI it is not the same as a boot flag on MBR. Partition tools call it that but it really is a gpt code ef00 in the partition type where the old MBR boot flag really was a partition setting in the partition table.

If you add boot flag does it boot?

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.


From liveCD you should be able to mount partitions if they now work and see files.

---

### Post by Cipher1874 on 2012-10-18
Alright, so after getting all the files out, I only have one final thing left to do, which is to repair / re-install the OS. I tried with the WIN7 ISO that I burned, and although it runs, it doesn't seem to fix the problem using startup repair and when I try to install the OS, it says that there is information missing (I can't remember the exact wording). So I'm guessing that it's just something missing from the ISO?

I'll try making a new one today using the WIN7 tool and the ISO on their website.

---

### Post by oldfred on 2012-10-18
While the Boot-Repair will only reinstall a Windows boot loader, not make other fixes to Windows, run the report just to document system and see what is where.

---

### Post by Cipher1874 on 2012-10-18
Run what report? You mean post the results of the startup repair?

---

### Post by oldfred on 2012-10-18
Post the link to the BootInfo report that this creates.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.

---

### Post by Cipher1874 on 2012-10-18
Alright, installing it and going to run it in a sec!

---

### Post by Cipher1874 on 2012-10-18
[http://paste.ubuntu.com/1288083/](http://paste.ubuntu.com/1288083/)

---

### Post by oldfred on 2012-10-18
It looks like a standard UEFI install with gpt partitions. 

But script is reporting these errors.

> Warning: /dev/sda contains GPT signatures, indicating that it has a GPT table. However, it does not have a valid fake msdos partition table, as it should. Perhaps it was corrupted -- possibly by a program that doesn't understand GPT partition tables.  Or perhaps you deleted the GPT table, and are now using an msdos partition table.  Is this a GPT partition table?                                                                             Error: Both the primary and backup GPT tables are corrupt.  Try making a fresh table, and using Parted's rescue feature to recover partitions. Download gdisk and run it, it may update gpt tables and repair them.
Or try parted's rescue feature as suggested by Boot-Repair.

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)

 GPT fdisk Tutorial -srs5694 in forums
[http://ubuntuforums.org/showthread.php?t=1439794](http://ubuntuforums.org/showthread.php?t=1439794)
[http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

gdisk is in the repository so you can add it to liveCD or USB from terminal:

sudo apt-get install gdisk

---

### Post by Cipher1874 on 2012-10-18
Okay, I'll try this next time I boot!

That fixed it, so now I'm actually able to boot the OS and everything is as it was before. Except one thing, now instead of just showing the C: drive, with 500 GB of space, it shows:
OS ( C: ) 100 GB free of 186 GB NTFS
SYSTEM ( D: ) 165 GB free of 196 GB FAT32
DATA ( E: ) 254 GB free of 254 GB NTFS
RECOVERY ( G: ) 11.4 GB free of 24.4 GB NTFS

Any reason as to why this may be?

---

### Post by oldfred on 2012-10-19
Not sure.

Testdisk may have changed some sizes.

Your actually had more than just c: before.  This is typical Windows partitions as suggested my Microsoft:
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx]("http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx")
Windows technical info on gpt and GUIDs
[http://msdn.microsoft.com/library/windows/desktop/aa365449](http://msdn.microsoft.com/library/windows/desktop/aa365449)

You may need to also add the MSR partition. It seems to be just space Microsoft wants and is not formated. It looks like it want only 128MB.

Was E: what you were planned as unallocated for Ubuntu? With gpt partitions there is no 4 primary partition limit so you can make as many partitions you want. Actual limit is 128 it you really want a lot. :)

You already have the efi partition. I normally suggest a shared NTFS for any data you may want in both Ubuntu & Windows. Then you can set the c: drive partition as read/only in Ubuntu to avoid issues or accidents of deleting something you should not.

Ubuntu only needs / (root), most have swap as another partition, and some have /home or other data partitions.

Herman on advantages/disadvantages of separate system partitions post#3
[http://ubuntuforums.org/showthread.php?t=1410392](http://ubuntuforums.org/showthread.php?t=1410392)
Install with creating partitions screen shots
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)

several threads where users installed UEFI with dual boot.
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post #52 superfreak on pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)

UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)

---

### Post by Cipher1874 on 2012-10-20
Here's what gdisk gives me.
> GPT fdisk (gdisk) version 0.8.1
 
 Type device filename, or press <Enter> to exit: /dev/sda
 Caution! After loading partitions, the CRC doesn't check out!
 Warning! One or more CRCs don't match. You should repair the disk!
 
 Partition table scan:
   MBR: MBR only
   BSD: not present
   APM: not present
   GPT: damaged
 
 Found valid MBR and corrupt GPT. Which do you want to use? (Using the
 GPT MAY permit recovery of GPT data.)
  1 - MBR
  2 - GPT
  3 - Create blank GPT
 
 Your answer: 

How do I set the data as read-only? And does that require ubuntu to be  installed, or is that still when it's running from the CD?

---

### Post by oldfred on 2012-10-20
gdisk has nothing to do with read only. Why are you wanting read only?

You have gpt partitioning so you do need to pick #2. If you pick number 3 you erase drive and #1 converts drive to MBR but booting then will not work.

I think you need the repairs for most applications to see drive.

---

### Post by Cipher1874 on 2012-10-24
Oh, sorry, I meant the C: disk on Ubuntu.

Alright, after I pick that, where do I go from there?

---

### Post by oldfred on 2012-10-24
I do not understand where you are at. There is no c: disk in Ubuntu. C: is Windows.

---

### Post by trusktr on 2012-12-03
This problem happened to me after trying to clone a Windows 8 UEFI disk to a smaller disk. Maybe that's why he's referring to C:?

---

