---
title: "M$oft win2k raid dead how to mount to ubuntu"
date: 2009-08-16
forum: General Help
---

### Post by 007casper on 2009-08-16
Is there a way to mount this hard drive on my other computer with ubuntu, and retrieve data? - if there is any at this point... 

Win2K did its obnoxious update, even though they dont support it.  Then, the raids went down to critical stage.
I have a hard drive for win2k, and a raid 1 with promise array for my own data.  I followed the instructions here [http://www.motherboardpoint.com/raid-array-off-line-p4c800-e-deluxe-t16546.html](http://www.motherboardpoint.com/raid-array-off-line-p4c800-e-deluxe-t16546.html)

I didn't have any other choice, because the raid went to critical stage, and couldn't access the hard drives.  I deleted the array and then redefine it.  When, the computer boots it goes to chkdsk... it seems as it is going through the array and it prints so fast I can barely make sense of it... it is something like "delete type file corrupt 48 init file 25st entry" Several hours passed it was still printing the same thing. I figured it is just toast.  I hit the reset switch.

I skipped chkdsk section.  Cleaned the system with advanced care... then reset again, it barely booted.

After it booted, I still cant access the two 1TB hard drive. It still says "the file directory is corrupted and unreadable".  I checked manage computer, and check the hard drive, it seems it is healthy but cant access it.  I think at this point my whole data is gone. I really don't think I have a virus, but it is really odd.

Is there a way to rescue the data in ubuntu by hooking the hard drive externally?

---

### Post by 007casper on 2009-08-16
I just installed the hard drive that was on my main computer with raid corrupt files to a computer with ubuntu.  It can see the drive, but cant access it.

I get this
> 
cannot mount volume
unable to mount the volume 'casper'

Details
Failed to open ntfs attribute:  No such file or directory Failed to mount
'/dev/sdb1': No such file or directory


I wrote sudo fdisk -l
> 
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00088542

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        2432    19535008+  83  Linux
/dev/sda2           60449       60801     2835472+   5  Extended
/dev/sda3            2433       60448   466013520   83  Linux
/dev/sda5           60449       60801     2835441   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xbc1018db

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1      121576   976559188+  42  SFS
/dev/sdb2          121577      121601      200812+  42  SFS


---

### Post by 007casper on 2009-08-16
sudo mount /dev/sdb1 /mnt/disk
> 
Failed to open ntfs attribute: No such file or directory
Failed to mount '/dev/sdb1': No such file or directory

:-(  ???

---

### Post by 007casper on 2009-08-17
Isnt there a way to read ntfs format hard drive?

I appreciate any input.  Thanks.

---

### Post by 007casper on 2009-08-18
I got an extra hard drive, I crossed my fingers, and figured I might be able to retrieve the data from my hard drive.  I wasnt able to format the new hard drive in the windows computer.  It just wouldnt see 1TB hard drive with usb hooked to it. Because of that I format it the new hard drive to NTFS over at ubuntu with gparted.  

I installed back the new hard drive to win machine via usb.  It saw it as a healthy hard drive.  I took it out, and follow the instructions [here]("http://ubuntuforums.org/showthread.php?t=449872"). It seemed to work without an issue.  However, now I cant mount the new hard drive in ubuntu and on the win machine.

I get this error... 
DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)

ntfs signature is missing.  Failed to mount '/dev/sdc': Invalid argument The device '/dev/sdc' doesn't seem to have a valid NTFS. Maybe the wrong device is used? Or the whole disk instead of a partition (e.g. /dev/sda, not /dev/sda1)? Or the other way around?

I just want to retrieve my old data.  Any suggestions how I can retrieve data from my old hard drive....

Thank you.

---

### Post by 007casper on 2009-08-22
is there any data recovery app for hfs file system?  

I have used ddrescue to clone the messed up drive.  However, the drive is dynamic and because of that I still cant access the data.  I couldnt find any app over at synaptic, maybe I am not looking at it the right way.

Does anyone know an app that will recover data?


Thank you.

---

### Post by P4man on 2009-08-22
did you try testdisk ?
[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)

its in the repo's.

---

### Post by 007casper on 2009-08-23
Thanks P4man!

Yeah, I saw it before but I guess I judge the book by its cover.  I have been trying many recovery apps and so far testdisk rocks compare to others.

I am having a minor issue though.

I am using testdisk in win2k instead of ubuntu, because thats what was recommended in various threads here and also with testdisk.  However, I am so ready to dump win...

I am constantly getting pop ups that states 
> Windows was unable to save all the data for the file \Device\HarddiskVolume2\$BitMap. The data has been lost.  This error may be caused by a failure of your coputer hardware or network connection.  Please try to save this file elsewhere.
 

or 

> Windows was unable to save all the data for the file \Device\HarddiskVolume2\$Mft. The data has been lost.  This error may be caused by a failure of your coputer hardware or network connection.  Please try to save this file elsewhere.

I checked the logs over at testdisk. It seems as any file name with a space is an issue. It just cant create the directory.

I thought of creating the directories manually.  And then I got this pop up...  
> Unable to create the folder 'New Folder'
The system cannot find the file specified

This might seem ignorant... is there a way to get rid of all the $Mft $BitMap and anything windows related tables?

---

### Post by P4man on 2009-08-23
I'm afraid Im probably more ignorant than you when it comes to raid..:s

is \Device\HarddiskVolume2\ your raid?
Have you been able to mount it, and is it writeable too?

id guess that popup means the volume is read only and something is trying to write to it. Is it possible one of the harddisks is failing and its a mirroring raid which is now in read only ?

> 
This might seem ignorant... is there a way to get rid of all the $Mft $BitMap and anything windows related tables? 

You mean..like, formatting it ? heh? Im not sure what you're asking.

---

### Post by 007casper on 2009-08-23
\Device\HarddiskVolume2\ maybe it is one of the raid drives...  I have raid 1 mirror (two hard drives)  

There should be a way to fix $Mft, $BitMap, and MftMirr or just to get rid off it. 

I thought \Device\HarddiskVolume2\ is my external drive where I am trying to load the data from raid drive.  Because it only happens when I tried to copy the data from raid to external drive. 

However, it is possible that raid is trying to load "copy" info to the mirror drive on raid, and if the hard drive is failing thats why I am getting that message.

The external drive is fine, seems to work.  However, somehow it gets unmounted out of the blue.

Regarding the raid drive... I might be wrong on this, however I think my raid hard drive is working fine without a problem.  I think $Mft tables are messed up on the raid. 

I was reading about that somewhere, but the solution didn't work.  All the raid hard drives are brand new, so is the external drive.  

Supposedly, it was very common with win2K to mess up the $Mft tables and then the raids wont be in sync, then the computer would print corrupted data.  Then, you can't access the hard drive.  When you click on the hard drive, it will say "The file or directory is corrupted and unreadable"

I guess vista had similar problems.  Good times...

the only reason I am using win2k is because of the certain applications I have works with win2k... 

I got this info from wikipedia regarding $Mft etc...
> 	$MFT 	Describes all files on the volume, including file names, timestamps, stream names, and lists of cluster numbers where data streams reside, indexes, security identifiers, and file attributes like "read only", "compressed", "encrypted", etc.

> $MFTMirr 	Duplicate of the first vital entries of $MFT, usually 4 entries

> 	$Bitmap 	An array of bit entries: each bit indicates whether its corresponding cluster is used (allocated) or free (available for allocation).

Any ideas the best possible way to retrieve data.... is there a way to retrieve the data with not including the $Mft, $MftMirr, $BitMap from the raid?

Thank you.

---

### Post by P4man on 2009-08-24
Im still not sure where you are now. You installed only one of the raid drives, and you're trying to retrieve the data with testdisk under windows ? Or does windows let you "mount" the drive and see the files? Not that I ever heard before of $Mf $BitMap or MftMirr, I guess its related to the raid.

---

### Post by 007casper on 2009-08-24
I was on windows.  I attached an external hard drive with usb. I tried to recover the files onto external drive from the raid with testdisk.  

Everything seemed to work fine in the begining.  I did quick search, then deeper search, then picked p on testdisk to see the files and copy files one folder at a time.  The first one worked without a problem. Then, when I was copying the second folder I started to get write delay pop ups stating error on $Mft.  Then, the external drive unmounts itself.  Reboot the computer, the computer shows external drive as corrupted.

I have been trying to figure out how to fix this issue here and there for a few days now. The awesome win operating system writes $Mft files, which is information on files with table structures.  I guess $Mftmirr is for the raid.  

I think those $Mft files are corrupted since the raids went of track due to win2k. Therefore, even if I back up the data to the external drive, I cant access these files as I stated before... because windows thinks the external hard drive is corrupted as well due to the bad $Mft information.

I used these instructions.
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

I thought about picking write, I guess that over writes MBR files.  I am not sure what MBR is... it seems it has to do with $Mft

However, cgsecurity doesnt have detailed documentation on this matter

The site states...
To actually write partition data to the MBR, you must choose the "Write" selection and press the Enter key. 

however, in another section under menu_analyse ([http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)) it states... 
Write
    Writes the changes that have been made in TestDisk's memory buffer to the hard drive. If you are unsure of the changes (often to the MBR's Partition Table), then don't use this function!

I am going to try to recover data on ubuntu without raid.  I cloned the raid drive a few days ago in ubuntu.  I am going to attached the clone drive internally, and try to recover the data to the external drive via usb.  The clone drive shows as dynamic drive because of $Mft information.

---

### Post by P4man on 2009-08-24
MBR is the master boot record. Its the first sector of your harddrive and has 2 main purposes: it holds the primary partition table and can contain a bootloader. The latter is irrelevant in your case, but if indeed the MBR is corrupted, its probably a good idea to let testdisk rewrite it, since it seems it figured out the partition table  correctly (as you can browse the disk with it). Even more so since you got a duplicate.

Running testdisk under ubuntu will probably yield the same result as under windows (except if windows keeps trying to mount the drive?)

---

### Post by 007casper on 2009-08-24
do you know what "L:load backup" does?

---

### Post by P4man on 2009-08-24
im guessing it will try and load a backup of the MBR. If there is one. 
(Or if you made one which is not likely).

---

### Post by 007casper on 2009-08-26
I used testdisk to recover from the clone.  It was partially successful.  Some folders were just empty.

Then, I took the raid and ran testdisk.  Smoooth operation... everything was there. However, if I try to move the recovered data to external drive and it unmounted itself.  I figured it is due to file names having spaces.  Any file or folder that has a space causes external drive to choke and then unmounts. 

Then, I unloaded (moved) the recovered data from raid to the computer's main drive that has ubuntu on it.  I moved as much data as possible to home folder without any problems.  I figured I would try to move it one more time from home folder to external drive.  It was without a success.

I tried to run ubuntu via live cd... same problem.  Actually, it made matters worse.  It corrupted the external drive.  Even though, I knew it wasnt the best choice... I ran sudo ntfsfix /dev/sdc1 (chkdsk just hangs on win)  The external drive got fixed.  Then, try to move the data again from... sudo mv /media/disk/user/backup/folder /backup_ 

it worked for a few folders.  Then, it started to unmount again.  I kept trying again, again.... then the whole drive collapsed.  

I quit working on live cd.  I rebooted.  Then, I tried to move through testdisk from raid to external drive.  It failed and collapsed the drive for good.

So, now I am running testdisk on external drive.  Because everything that I moved is gone on the external drive.  I need to move the data from home folder to an external drive.  I am running testdisk to see if it will get picked up.  At this point I can reformat the external drive again.

At the moment, majority of the files from win is on home folder.  I have been trying to move these files without success to an external drive.  I even installed the external drive as internal drive.  No luck!

How can I solve this issue at hand?

Thank you

---

### Post by P4man on 2009-08-26
What do you mean it "unmounts"? testdisk doesnt work on mounted volumes afaik, it accesses the disk directly.

also what do you mean by "unload" ?

---

### Post by 007casper on 2009-08-26
You are right.  Sorry about that... testdisk works without mounting the drive.   I meant that the whole drive disappears.   It doesnt show up through the terminal. 

If I use live cd, and mount /media/hda1 /dev/hda1 and then try to transfer the files through the terminal.  The external drive just gives up and disappears when it hits file names with spaces.  I figured using testdisk will save the day by moving files from the main drive to the external drive.  However, the external drive just disappeared.  And, now it is pretty much damaged all the way. 

I am happy to have some of my files back from the raid drive.  It just seems unfortunate that I cant move these files.  

It seems as there is a hick up in the whole process. When I am trying to transfer these files from ext formatted main drive to the external ntfs drive, the drive gets damaged. I guess I could reformat the external drive.  I read that you should never save the same data to the damaged disk regardless if it is formatted or not... 
  
unload = move

any suggestions?

thank you

---

### Post by P4man on 2009-08-26
I thought you had already done this, but maybe I am mistaken? The first thing to do is always making a byte copy of the problematic drive (to a known good drive of course). you can do that with "dd" (perhaps also in testdisk im not sure).

Google for dd is you're not familiar with it. If you're having trouble make a byte copy with dd, try ddrescue (its in the repo's). I never tried it myself tho.

Once you have a dd image, then you can use testdisk and photorec on the original or on the copy to try and recover your files without doing any additional harm.

As for what is going on with your drive or machine, I got no clue. I never saw drives disappear like that. If you do fdisk -l, the drive no longer shows up ? Or is just that it gets unmounted, which would be more understandble for a problematic drive. You shouldn't mount it to begin with :s

---

### Post by 007casper on 2009-08-31
if I hook up the hard drive with sata cables internally. It works.  I can transfer files to it.  

However, if I hook up the hard drive externally via usb, it unmounts itself when large files are transferring.  If I do fdisk -l, it also doesnt show anymore.  If I reboot the computer, it is still not mounting.  I have to pull usb cable, then reboot the computer.  Then, I plug the usb cable, then the hard drive shows up... then try to transfer the files... if the folder is under a gig, it transfers.  If it is over one gig, it chokes itself, and unmounts.

---

### Post by P4man on 2009-08-31
the USB enclosure, does it have its own power supply?
If not, your usb ports can probably not supply enough current, and that may well be your problem. Even if it has its own power supply, it might be faulty

---

### Post by sloggerkhan on 2009-08-31
Slow down and take a deep breath. Your posts are so frenetic I can't tell exactly what is going on.

So far I've gathered you have a windows 2000 computer using a RAID 1.
So question #1: What were you using as a raid controller? Hardware RAID?
Question #2: are you saying your RAID is still working, just that the data on it is corrupted?
Question #3: Can you access either drive of your RAID 1 in single disk mode?
Question #4: Have you run any disk repair utilities?
Question #5: How old are the disks and what does a smart test say about them?

Really I think you need to slow down and communicate a clearer picture of your situation, if you aren't careful you could make things worse.

---

