---
title: "Entire hard disk wiped out! Please help"
date: 2006-04-24
forum: General Help
---

### Post by daiwai on 2006-04-24
edit: Problem solved [http://ubuntuforums.org/showpost.php?p=955658&postcount=18](http://ubuntuforums.org/showpost.php?p=955658&postcount=18) thanks for all the help, this is a great community :)


I'm using kubuntu bb 5.10, koffice is the latest release (1.5)

Here is what happened:

I downloaded a zipped Excel file and opened it in ark. 
Then in ark I selected open with .. from the excel file's context menu and chose kspread. kspread started loading but it was just a blank window, that was not redrawn.
I went back to ark and this time selected open with openoffice calc. calc started loading but the progress bar in the slash screen got stuck at around 80%.
At this time kspread was still open and the system became very unresponsive with heave harddisk activity.
After ~3 minutes i rebooted the machine.

Now the bootloader is still there but kubuntu won't start (forgot to note the exact error message, but it is caused by the hd being completely empty :O )

I booted to winxp and the harddisk (that had once contained my kubuntu installation :-s) is shown as not initialized and has no partitions.

any help appreciated.
thanks in advance

---

### Post by blssurfer on 2006-04-24
Sounds bad, try to mount the disk booting with a linux CD distribution, run chkdisk and all that stuff on the partition.

Never use root for that risky stuff. Also your hardware may have collapsed, turn of the machine just in case.

---

### Post by blssurfer on 2006-04-24
Windows newer will show any linux disk as a working partition...

---

### Post by gingermark on 2006-04-24
[QUOTE=blssurfer]Windows newer will show any linux disk as a working partition...[/QUOTE]
Although there are drivers for Windows available so that it can read and write to ext2, and by extension ext3 I think.

---

### Post by daiwai on 2006-04-24
Thanks for your reply.
It was not entirely linux disk. It had a big NTFS partition, one FAT32 and then the ext2 and swap for kubuntu.

I just wonder how that could happen :-?

---

### Post by brallan on 2006-04-24
so you have two hard drives or just one with 4 partitions?

---

### Post by daiwai on 2006-04-24
Yes, I have two hard drives. One has winxp installed, nothing happened to that drive. the other has the linux and some data partitions as described above.

---

### Post by brallan on 2006-04-24
and windows does not assign either the NTFS partition or the FAT32 partition a drive letter?

Its probably a bit late to say it now, but one thing about Ubuntu system crashes, is that you often can still press CTRL-ALT-F1 to get to the (tty1) terminal (CTRL-ALT-F7 is tty7 - X windows) instead of powering down. CTRL-ALT-BCKSP also is sometimes useful, to restart X windows.

---

### Post by souki on 2006-04-24
that's crazy!

it once append to me on a hardware raid array, something went wrong between postgres and the raid.

do you have something specific with your hardware ?
I hope you will at least find the reason of this, that's too bad

---

### Post by daiwai on 2006-04-24
Yes, windows says not initialized and 152,6GB not allocated, no partitions. I also booted a kubuntu live cd and checked in system settings > drive management(?) there it also did not list any partitions.

edit:
@ souki

nothing specific with my hardware as far as i can tell. the drive is a 160gb ide drive, no raid or something like that.

yes, I have no idea what might have caused this. looking at it now, maybe it would have been better to turn the pc off immediately when i saw that the programs were not loading. on the other hand i am not sure if those two programs were really the cause of it.

---

### Post by brallan on 2006-04-24
Ufff. sounds like a hardware failure. hope there wasn't anything terribly important on that drive.

---

### Post by daiwai on 2006-04-24
I just run testdisk on the drive and it says the structure is ok, i did not find any partitions though. :(

There are some important files on that disk, so I am still hoping to get some of it back. the ironic thing is that i have some backups on the same disk (but different partition), as the windows drive is quite small.

---

### Post by syg00 on 2006-04-24
[QUOTE=daiwai]Now the bootloader is still there but kubuntu won't start (forgot to note the exact error message, but it is caused by the hd being completely empty :O )
I booted to winxp and the harddisk (that had once contained my kubuntu installation :-s) is shown as not initialized and has no partitions.[/QUOTE]Does this mean the menu displays, _and_ you are able to boot XP from it  ???.
Which loader are you using  ???.

Can you also expand on your comments on testdisk results  ???.
Are you saying an analyze found *_NO_* recoverable partitions  ???.

What does "sudo fdisk -l" produce ??? (that's an ell as in list)

---

### Post by daiwai on 2006-04-24
The bootloader is grub, it is installed on the same disk as windows, i think. It loads the usplash and shows loading modules .. ok and then when initializing deb/ it stops, goes to textmode and shows some error messages FATAL error message. 
then there is an error about it could not load tty and it shows a command prompt. i did a 'ls' and there are some folders of the root file system.



```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/hda: 20.4 GB, 20496740352 bytes
255 heads, 63 sectors/track, 2491 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1020     8193118+   7  HPFS/NTFS
/dev/hda2            1021        2491    11815807+   f  W95 Ext'd (LBA)
/dev/hda5            1021        1785     6144831    7  HPFS/NTFS
/dev/hda6            1786        2491     5670913+   b  W95 FAT32

Disk /dev/hdc: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/hdc doesn't contain a valid partition table

```

---

### Post by mjm115 on 2006-04-24
I would use Knoppix or PCLinuxOS or another LiveCD to see if you can view the files on the drive.

---

### Post by daiwai on 2006-04-24
Thanks for your suggestion mjm115, I will try that tomorrow.

syg00, here is what i did in testdisk (windows version, 6.3)

- select drive -> proceed
- select partition table type -> intel/pc partition selected
- analyze -> it shows partition sector doesn't have the endmark 0xAA55
--> proceed, now it is analyzing.
edit: displayed: structure ok -> no partition found or selected for recovery

running the search now.

---

### Post by syg00 on 2006-04-25
[QUOTE=daiwai]
- analyze -> it shows partition sector doesn't have the endmark 0xAA55[/QUOTE]Erkkk !!!!
Seems somebody started overwriting the disk - depending on how for it got will decide on what's left.
Don't like testdisk not finding anything though - but I've never used the Windows version. I _always_ keep a Knoppix disk handy - you can run testdisk (amongst a ton of other recovery) from it.
The fact that grub even shows a menu means that (at least) some of the data is still there. It uses direct sector addressing to find it's stage2/config. - even on a separate disk.
Try the folllowing from a liveCD and post the result```
dd if=/dev/hdc bs=512 count=1 | hexdump -C | less
```(you'll need root access)

---

### Post by daiwai on 2006-04-25
OK, now that is weird. The drive is back and working. :)

When I turned on my pc this morning I booted it to windows to see if I could recover some files from the disk. Anyway after I some tool (getdataback) finished running I wanted to save some of the files it found and saw all the partitions from the "broken" drive showed up in the explorer again. Rebooted to kubuntu and everything is there.

I've to admit I feel kinda stupid now :-s I still have no idea what caused all that. Must have been something that put the hard disk in some weird state. Anyway I'm going to backup some data now, just in case ;)


Big **thanks** to all who helped me with this (non-existent) issue, and sorry for wasting your time.

---

### Post by syg00 on 2006-04-25
[QUOTE=daiwai]Anyway I'm going to backup some data now, just in case ;)[/QUOTE]Now, and (at least) once a week - _ever_ week.

---

### Post by syg00 on 2006-04-25
[QUOTE=daiwai]Anyway I'm going to backup some data now, just in case ;)[/QUOTE]Now, and (at least) once a week - _every_ week.

---

### Post by coolclassic on 2006-04-25
It is possible you have a lose connection that caused your HD to falter.

The next time Ooo freezes on you try using top or ksysgaurd to kill process.
If Ooo can not read a file it can attempt to open it and it will use all your processing power in it's attempt, slowing the system down.

---

### Post by !nkubus on 2006-04-25
I had similar tyroubles with kubuntun dapper beta and expresso, and I fired up Knoppix and ran:

gpart -W /dev/hda /dev/hda

answered the questions and then rebooting and everything was back to normal.

hope it helps in that case

---

### Post by shamrock_uk on 2006-04-25
[QUOTE=syg00]Erkkk !!!!
Seems somebody started overwriting the disk - depending on how for it got will decide on what's left.
Don't like testdisk not finding anything though - but I've never used the Windows version. I _always_ keep a Knoppix disk handy - you can run testdisk (amongst a ton of other recovery) from it.
The fact that grub even shows a menu means that (at least) some of the data is still there. It uses direct sector addressing to find it's stage2/config. - even on a separate disk.
Try the folllowing from a liveCD and post the result```
dd if=/dev/hdc bs=512 count=1 | hexdump -C | less
```(you'll need root access)[/QUOTE]

Would you mind explaining what the above command does?

---

### Post by daiwai on 2006-04-25
Thanks for the tip, coolclassic. I'll have a look if all the cables are properly plugged. When I tried to open the process table with ctrl+esc it was already too late, Ooo had already eaten up all system resources.

edit:
Inkubus, the problem solved itself, please see the previous page of this thread. Thank you anyway. Maybe I should edit my originial post.

---

### Post by syg00 on 2006-04-25
[QUOTE=shamrock_uk]Would you mind explaining what the above command does?[/QUOTE]Merely displays the MBR sector - I was planning on checking it was sane.
No need anymore.

---

