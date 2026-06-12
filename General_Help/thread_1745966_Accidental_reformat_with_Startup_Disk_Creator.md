---
title: "Accidental reformat with Startup Disk Creator"
date: 2011-05-01
forum: General Help
---

### Post by Electric.Head on 2011-05-01
Hello, I did a bad thing and wonder if anyone can help.  

I wanted to check out 11.04, so attempted to use Startup Disk Creator to put the ISO onto a dedicated partition on my 500GB USB External HDD. The 500GB drive WAS (you might be able see where I'm going with this) split into 4 partitions: 

[LIST=1]
[*]Large partition containing old files/backups (~450GB NTFS)
[*]Small partition containing documents and images (~10GB EXT3 or EXT4, can't remember)
[*]1 CD sized partition (~750MB)
[*]1 DVD sized partition (~4.5GB)
[/LIST]
I selected the 3rd partition in Startup Disk Creator to place the contents of the 11.04 ISO, it warned me that it was going to erase the contents of the disk and, paying attention to this warning fully ](*,), I confirmed, and the entire 500GB turned before my eyes into one FAT32 partition. I promptly panicked and restarted but no dice. I'm not going to bitch at the illogical nature of it reformatting the entire disk, even with the warning, rather just attempt to do what I can to recover.

Now, with relative ease I've recovered from a similar mistake before using testdisk, but in that case I think I just deleted the partition table and then recovered it. This time, I'm not sure how to proceed. Whilst I would obviously like to recover the large NTFS partition, I'm  very keen on getting the second EXT? partition back or at least  recovering some of the data, the last two don't matter whatsoever. 

Running testdisk just seems to find the FAT32 partition and stop. I've currently selected the disk, changed the partition type to NTFS, and am now doing a deep scan to see if it turns up the old partition but nothing's happened yet. 

Any advice on how to proceed? Do I want to delete the FAT32 partition then use testdisk or is that a bad idea? I don't have the disk space to clone the drive as a safety net sadly...

Fingers crossed someone can assist.

---

### Post by dragonfly41 on 2011-05-01
Photorec seems to be favourite for data recovery in posts in this forum ..

but Photorec recovers files which lose their file names.

[http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive](http://www.linux.com/news/enterprise/storage/8257-how-to-recover-lost-files-after-you-accidentally-wipe-your-hard-drive)


> 
PhotoRec recovers files by finding deleted files and copying them to  disk. This means that files should not be recovered to the same disk  partition on which the deleted files reside (unless you're recovering  from a disk image file), because that could lead to the deleted data  being permanently overwritten.
Another important thing to remember  is that PhotoRec will most likely recover a lot of files. This means  that the partition on which the recovered files are to be stored should  have at least as much free space as the size of the partition on which  PhotoRec is searching for recovered files.

Since your 500 GB drive is external USB drive .. can you connect it to a working windows environment and try the evaluation version of recovermyfiles 

[http://www.recovermyfiles.com/](http://www.recovermyfiles.com/)

At least you can analyze at no cost to first see if you can recover. 

Recovermyfiles can selectively recover files after first scan .. and their filenames are usually recovered.

---

### Post by Electric.Head on 2011-05-01
Thanks. I'm vaguely familiar with photorec as I think I tried it before on the last mishap before successfully recovering the partition. As I remember it, it's pretty much a brute force approach so preferably I will leave it until I've ruled out recovering the partitions. 

I will try accessing the drive from Windows using trial software to see what's there - good idea.  

If anyone has any advice on recovering the partitions in particular rather than recovery in general that would be ideal (even if it's just "you probably can't").

---

### Post by dragonfly41 on 2011-05-01
You can try this too ..

[http://www.findandmount.com/](http://www.findandmount.com/)

---

### Post by Electric.Head on 2011-05-03
As it frustrates me no end when I see threads like this on forums which seem relevant to me and are never closed or expanded on, here's an update: 

**Recovering the original partitions**

Currently I've managed to retrieve my important (2nd) partition (which was actually NTFS, not ext3 or ext4). I'm slightly hazy on *exactly* what I did as regards to specific selections/options, and I'm not in front of TestDisk to check the easily accessible ones, but for the sake of posterity an overview is as follows: 

TestDisk was only finding the single, disk-wide FAT32 partition, I set the Type to NTFS and did a deep scan. It eventually found the all partitions (including the FAT32), so I set the FAT32 partition to "D" or Deleted, and set the original 4 to "P" or Primary. The 2nd partition actually seemed to come up twice, covering an identical subset of the HDD, but one I could list files and the other I couldn't (error: "Can't open filesystem. Filesystem seems damaged."). Just to be sure I copied these files I could list (which seems to be everything I had on there) off onto another drive using TestDisk's copy functionality and set the non-working "ghost version" of the partition to Deleted. 

So far so good, most important stuff salvaged. Unfortunately, TestDisk also failed to list files for the large NTFS partition (1st in my list, error: "Can't open filesystem. Filesystem seems damaged.") but I decided to soldier on and write TestDisk's new partition table to the disk and reboot to see what happens (as far as I understand it I could just repeat the process *if* nothing's been written to irrecoverable bits of the drive in doing this). Rebooting allowed me to mount partitions 2 through 4 successfully with no problems, but although the 1st partition was proportioned correctly, looking at it in Ubuntu's Disk Utility it was flagged as NTFS but Unallocated. Attempting to replace the Boot Sector for this partition with the backup in TestDisk didn't work (no failure per se, it claims both BS versions are OK and identical). This is where it gets hazy (i'll try to update with something more solid after reviewing the options), the MFT had some sort of error and TestDisk was unable to do anything with it, which is why the filesystem is "damaged" I guess. 

At this point, although I suspect some tweaking could be done to attempt to retrieve that NTFS partition (the "recovered" partition starts at, what seems to me as a layman, at an odd sector: 77 not 0 or otherwise at the very start of the drive) beyond my capability, I've all but given up trying to restore the partition as-is and have resorted to file recovery at this point to try and salvage what I consider worthwhile. If I manage to pull everything off that I think is worth it, I may attempt to revisit restoring it to it's original form for the sake of experiment.   

For what it's worth, Partition Find and Mount from a Windows 7 installation couldn't do anything at this point, it was unable to mount the faulty NTFS partition (perhaps unsurprisingly maybe it might have had better luck before using TestDisk on it). 

**File recovery**

I've opted to avoid using PhotoRec, as although I suspect it will "work" 350+ GB of files which are straight up copied remnants of old operating system installations / home directories that I haven't got round to sorting through the dregs of, videos, a backup MP3 library, and a ton of old archived programs are not going to be amenable to being recovered as random files in no directory structure. 

I ran the trial version of Recover My Files but it was just bringing up a list of random filenames similar to PhotoRec so I promptly abandoned that. Currently running a scan with the trial version of the program GetDataBack which claims to recover filenames and some semblance of directory structure, unfortunately it doesn't return live search results so I have some hours to wait before I can see what it's turned up and how it's turned it up. I'll update.

---

