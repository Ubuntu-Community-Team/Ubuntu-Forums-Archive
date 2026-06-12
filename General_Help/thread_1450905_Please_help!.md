---
title: "Please help!"
date: 2010-04-09
forum: General Help
---

### Post by nickxjones on 2010-04-09
Well, to start off, I consider myself a relatively tech savvy person. So prior to installing ubuntu on my MacBook Pro, I ignored all of the warnings to back up my hard drive, which I didn't do. So if I am a lost cause, I will accept it, but I'd like to know for sure.

I installed ubuntu today from a live cd, and it is running just fine. My problem is that I am not able to get back to Mac. The computer boots right into ubuntu. What I'm hoping is that Mac OS X, and all of my files, are still safe somewhere on my computer, and not gone forever. 

Sorry in advance if this is an already-addressed-topic, but Google didn't yield me any results, so I'm depending on you guys.

Thanks in advance, and feel free to ask me for any more system specs you may need to better solve my problem.

Nick

---

### Post by lisati on 2010-04-09
Which version of Ubuntu are you using? When you installed, did you tell the partioner to use the whole disk?

There's usually an option to choose between the different OSes on your computer when you boot.

---

### Post by nickxjones on 2010-04-09
I'm not sure where the OS indicates which version of ubuntu I'm using, so I can't tell you. It's the newest one I assume, I just installed it today. There is no option to choose between different OSes on my computer upon startup.

---

### Post by jobix on 2010-04-09
Can you check and see what the output of the "df -h" command is? Run it from the command line in a terminal. See if it shows you any filesystems that might look like your mac partition. You can use the "ls" command to show the files in any of those filesystems. Another (longer) way to do this would be to execute a "find" command and try to find a file that you know exists on your mac system. Use / as the root to search from.

---

### Post by sarloth on 2010-04-09
> **nickxjones said:**
> Well, to start off, I consider myself a relatively tech savvy person. So prior to installing ubuntu on my MacBook Pro, I ignored all of the warnings to back up my hard drive, which I didn't do. So if I am a lost cause, I will accept it, but I'd like to know for sure.

I installed ubuntu today from a live cd, and it is running just fine. My problem is that I am not able to get back to Mac. The computer boots right into ubuntu. What I'm hoping is that Mac OS X, and all of my files, are still safe somewhere on my computer, and not gone forever. 

Sorry in advance if this is an already-addressed-topic, but Google didn't yield me any results, so I'm depending on you guys.

Thanks in advance, and feel free to ask me for any more system specs you may need to better solve my problem.

Nick

It would help if you knew what options you chose when installing Ubuntu. Since you don't appear to, please post the output of the following command:

```
sudo parted /dev/sda print
```

What you are doing with this is listing the partitions on your hard drive. I am assuming your only hard drive is /dev/sda. If you know it is something different, use that instead.

If you see this listing any partitions with the File System "HFS" then you should still have your OSX and documents on the machine, you simply need to add OSX to GRUB2.

---

### Post by Iowan on 2010-04-09
> **nickxjones said:**
> I'm not sure where the OS indicates which version of ubuntu I'm using, so I can't tell you. Should (also) be available under System>About Ubuntu.

---

### Post by nickxjones on 2010-04-09
Iowan, I'm running 9.10.

Jobis:
Your /insert filename here suggestion resulted in "No such file or directory"

...it's not looking good so far


Sarloth:
administrator@Nick-Jones:~$ sudo parted /dev/sda print
[sudo] password for administrator: 
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  40.1GB  40.1GB  ext4

administrator@Nick-Jones:~$ 

My hard drive's maximum capacity is over 300 gs, just to let you know. Prior to installment, I partitioned my hard drive to have 40 gs aside for ubuntu, leaving the rest for Mac OS X. This was completely before I installed anything related to linux.

---

### Post by lidex on 2010-04-09
What is the output of this command:
```
sudo fdisk -l
```

---

### Post by JJJCR on 2010-04-09
hi nickxjones, not a tech savvy on linux, but have you tried to install grub so the system will prompt you which OS to load during boot up.. 

maybe can ask guys around here to guide on how to install GRUB for dual booting.. Goodluck!

---

### Post by nickxjones on 2010-04-10
Yeah, I'm not really sure how to install Grub. I'm not sure which one to install, Grub Legacy or Grub 2, and when I click on either of them, it brings up a long list of downloads from an ftp site, so it makes it even harder to pick which one would be right for me.

On another note, when I do boot up my computer, the first thing that happens is that I get the white screen that happens when Mac OS X normally boots up. I'm not sure if this would still happen with just ubuntu installed, or if it's just permanently written into the hard drive somehow so no matter what OS is being booted, that is the first screen. It doesn't get to the point with the black apple and the progress bar; after the white screen appears the screen goes black and then the ubuntu boot up occurs. There is no menu in between these two processes.

And lidex, the output of that command yields:

administrator@Nick-Jones:~$ sudo fdisk -l
WARNING: GPT (GUID Partition Table) detected on '/dev/sda'! The util fdisk doesn't support GPT. Use GNU Parted.


Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        4872    39132813   83  Linux

---

### Post by nickxjones on 2010-04-10
I'm not sure how this forum feels about bumping threads, but this is a big problem for me that needs to be fixed (if possible) as soon as possible. Seeing as this is such an active forum, and threads get buried so easily, I'm hoping it won't be too much of a problem, but if it is I apologize in advance.

---

### Post by misterbk on 2010-04-10
Nick,

You need to do this command:

sudo parted /dev/sda print


Can you remember how you made the partitions?  If you cleared out the partition table and made a new partition for Linux, your files are gone.  If you resized an existing partition and left room at the end for Linux, you might be fine.

---

### Post by nickxjones on 2010-04-10
"sudo parted /dev/sda print"
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  40.1GB  40.1GB  ext4

I made the partition in Mac OS X with Disk Utility, leaving 40 GB or so for Linux. But, I'm not sure if somewhere along the ubuntu installation if I possibly made a mistake as to which partition I put ubuntu in. But, linux does recognize that it only has 40 GB, and that the hard drive is 320 GB. I just have no way to access what's in the other 280 or so.

---

### Post by misterbk on 2010-04-10
Sorry just noticed the other post where you pasted the parted command results.  It was formatted similarly enough to the 'fdisk -l' that I missed it.

Parted should have reported any other partitions.  I think you may have borked your drive.  I'm not familiar with Disk Utility.  If you opened up Disk Utility and used it to create a brand new partition table with 40GB at the beginning of the disk for Ubuntu (it looks like this is the case) then what you have done is erased your OS-X partition and its data and overwritten it with the Ubuntu partition and data.  I'm not sure how you did that from within OS-X though because most sensible OS don't let the user un-partition the system drive from inside the OS.

We need more specifics from you.  I'll try explaining what you should have done, to make it easier to tell us what you really did do:

You probably (but we don't know for sure) started with the whole drive partitioned for OS-X.

You should have used Disk Utility to shrink down your OS-X partition, without deleting it and without re-making the whole partition table.  That should have created about 40GB of free space at the END of the disk, leaving your Mac OS-X partition at the beginning of the disk taking about 280GB.

You should have booted up to the Ubuntu install disk.  When it came to where to put Ubuntu, you should have selected the existing 40GB partition at the END of the disk.  (You should NOT have deleted any partitions, and should NOT have re-created a new partition table.)  During this process you should have been able to see a 280GB partition at the beginning of the disk as well as the 40GB partition you made.

Alternatively, you should have resized the OS-X partition using the Ubuntu installer, but I don't know if or how well that works.  (Haven't tried it.)

Somehow, you seem to have ended up with a 40GB partition at the beginning of the disk, and no other partitions.  That probably means you obliterated the existing Mac partition and made a whole new partition table.  Don't know if you did that from within OS-X or within the Ubuntu installer, but unless you somehow shrank the OS-X partition to the end of the disk and parted is glitching and now showing it, OS-X is gone now.

If you want to try and get things back, you'll want to start the mac up in "firewire" mode (hold T at start, I think?) and plug it into another Mac using a firewire cable.  You might magically see your mac files, but I kind of doubt it.

If you don't see your files and you REALLY NEED THEM, you will want to find a recovery program that can recover from HFS+ filesystems.  Emphasis you only do this if you REALLY NEED the files.  It is a very long, time-intensive process and there is no guarantee of success.  You'd be relying on the shred of hope that you have only written new data over the operating system files and some programs, leaving your user data intact, and also relying on the recovery software to be able to figure out those folders exist since the main filesystem data has been erased.  I have had some good luck with this in the past, and some bad luck.  In every case it took three to six days of work.

On the bright side, you are now slightly more tech savvy than when you started, because now you know why everyone says you ALWAYS back up your files when you mess with partitions!

---

### Post by lidex on 2010-04-10
Try this:
```
sudo update-grub
```
Watch the terminal to see if it updates your config. Reboot. If you don't see grub menu try holding down shift key after bios screen.

---

### Post by JJJCR on 2010-04-11
> **nickxjones said:**
> "sudo parted /dev/sda print"
Model: ATA Hitachi HTS54323 (scsi)
Disk /dev/sda: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
 1      17.4kB  40.1GB  40.1GB  ext4

I made the partition in Mac OS X with Disk Utility, leaving 40 GB or so for Linux. But, I'm not sure if somewhere along the ubuntu installation if I possibly made a mistake as to which partition I put ubuntu in. But, linux does recognize that it only has 40 GB, and that the hard drive is 320 GB. I just have no way to access what's in the other 280 or so.

hi nickxjones, it looks like that there's only one partition in your system but never tried dual booting with MAC OS before.
 normally it would display something like this if there are two partition or more like: /dev/sda1 /dev/sda2 but don't know if MAC file system is being displayed if you execute the fdisk -l command.

anyway, check out this link it might give you an idea on how to install GRUB: [http://www.linux.org/docs/ldp/howto/Multiboot-with-GRUB-2.html](http://www.linux.org/docs/ldp/howto/Multiboot-with-GRUB-2.html)

---

### Post by misterbk on 2010-04-12
I highly recommend attempting to retrieve your files BEFORE MAKING ANY FURTHER CHANGES TO THE DISK.

If there is a partition there and Ubuntu doesn't know how to see it, Ubuntu does not know how to deal with it.


If you are going to try to retrieve your files you need to do it NOW.  Before you boot up the computer, before you mess with Grub, before doing anything that writes more data to the disk.


What the people making recommendations about fixing Linux are missing is if you have only written 7GB to that Ubuntu partition, the remaining 33GB still contains Mac files.  The filesystem is blown away sure, but there is data everywhere on the disk that Ubuntu has not overwritten yet.  Disk recovery tools like R-Studio can find those and allow you to copy them to a spare disk if they are still intact.  (Not sure if R-Studio has HFS+ but I think it does.  It also costs money.  My search for something free hasn't had great success.)

If you're going to count the files as lost and steam on ahead, then no worries.

---

