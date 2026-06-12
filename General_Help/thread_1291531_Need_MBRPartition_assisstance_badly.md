---
title: "Need MBR/Partition assisstance badly"
date: 2009-10-14
forum: General Help
---

### Post by speed32219 on 2009-10-14
I was building a new PC and thought I would install a fresh copy of intrepid on a usb stick.  It worked and everything is great as far as the usb stick and it boots just fine using the new pc build.  I wanted to get all the kinks out so when I actually moved everything over to the new HD it would be squeaky clean with everything working.

Well, now the PC that has a dual boot XP SP2 and Intrepid image that I used to make the bootable USB stick does not boot. It just displays gparted.  Yes, just the word gparted. (I used a live CD to boot into ubuntu and did a manual partition on the usb stick that I always do).  I just might have fat fingered something, well I guess I did huh?

The PC has 2 160GB HD's, sda1 (c) and sdb1(d).

Now, when I boot using the Live CD it only mounts sdb1 (D) as sda1 (C) and gives me an  error if I try and access the real sda1 or C drive. I tired editing fstab and making a mount point, but I get an error that says "device /dev/sdb1 does not have a valid NTFS" maybe you selected the wrong device or the whole disk instead of a partition". (SDB1 rather than SDA1 because SDA1 is working as my 2nd drive) Kinda confusing.

OK, when I use gparted and check the drives, /dev/sda1 is OK, /dev/sdb1 has the ! point symbol and shows, ntfs filesystem, 149.04 GB size, --- used, --- Unused, boot Flags. (This is my C drive)If I double click on the partition a window opens and gives me a warning of "Invalid argument, failed to mount .dev.sdb1, the device doesn't have a valid NTFS.  Failed to startup volume ERROR(22).   IF also states that the error might occur if the disk was incorrectly repartitioned. (see the ntfsresize FAQ)

I will post some output cmd info next.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe2dd3c35

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19457   156288321    7  HPFS/NTFS

Disk /dev/sdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc2df8f3f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       19456   156280288+   7  HPFS/NTFS

Disk /dev/sdc: 2051 MB, 2051014656 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e558f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         231     1855476    b  W95 FAT32
/dev/sdc2             232         249      144585    5  Extended
/dev/sdc5             232         249      144553+  82  Linux swap / Solaris

ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=312576642, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=312560577, Id= 7, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0

ubuntu@ubuntu:~$ sudo parted /dev/sda1 print
Model: Unknown (unknown)
Disk /dev/sda1: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  160GB  160GB  ntfs              

ubuntu@ubuntu:~$ sudo parted /dev/sdb1 print
Model: Unknown (unknown)
Disk /dev/sdb1: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  160GB  160GB  ntfs

---

### Post by TiredBird on 2009-10-14
I'm not sure I understand what you're doing or what your problem is but I do have a considerable amount of experience with multiple partitions, dual boots and MBR's. I may not be able to help but I'll try.

Why don't you start by telling me what you are trying to accomplish and what you think you have on your hard drive. Try to keep it simple (I'm stupid you see). Once I understand what we're looking for, the info you have already provided will probably help. Right now though, its just scaring me, probably others too. Probably why you're not getting any help.

---

### Post by speed32219 on 2009-10-14
dual boot pc, XP SP2 and Ubuntu Intrepid 8.10.

Turn PC on, I usually get a screen that allows me to boot either XP or Ubuntu with a default of XP.  The PC is mainly used with XP and occasionally Ubuntu.  Most all other PC's on the network are running Hardy and Intrepid.

I put a Ubuntu 8.10 Minimal live CD in and a usb 8GB flash drive in a USSB slot and turned the PC on. Live cd asked me did I want to try it or install.  I installed the mini Ubuntu version with ssh server, no gdm, gnome, etc  it is a front end media pc.  When it came up to the partition prompt I selected manual on the 8GB USB drive.  Created 3 partitions, root, home, & swap. When it was time to write the MBR I couldn't remember the drive designator, so I selected sdc1 and I guess I was right because it wrote the MBR to the USB of which I can boot from right now.

Somewhere during the creating of the partition and MBR process  on the 8GB USB drive I must have depressed a wrong key, I really don't know, but now my main XP (with dual boot Ubuntu) will not boot.  Instead of the usual 1. XP and 2. Ubuntu selection screen, it just displays either Grub or Gparted.  I will shut it down and reboot to find out exactly what the word is. And if I boot from the Ubuntu Live CD it only shows one mounted HD whcih happens to be Drive D or the 2nd drive  but not the main Drive C.  So I can not mount Drive C (which is SDB1 now), the system gives me errors, check above post. 

Now the  first post of mine are the steps I have looked at to see what the problem could be and if it's fixable.  On SDB1 (Original C drive) it shows ntfs with proper cylinders, blocks but NO used or available drive space. I think I lost my partitions but did not want to try and recover using Gparted or XP without some expert advice.  I did a noob thing, I have not backed up some crucial data for the last 2 months. Ouch!

---

### Post by TiredBird on 2009-10-14
> **speed32219 said:**
> ...Most all other PC's on the network are running Hardy and Intrepid...

What are these others PC's. Are they part of your home network, is it business network, or what? I ask because there might be something on them that can be of help.

> **speed32219 said:**
> ...it just displays either Grub or Gparted...  

It is important that you find out which. Grub I can understand but coming up with Gparted on the boot would be puzzling indeed.

> **speed32219 said:**
> ...I think I lost my partitions...

They are probably not lost, unless you have done a lot of fritzing around with the disk after you discovered the problem. 

Unless the disk itself actually cratered, which doesn't seem very likely from what you have said, its doubtful if anything has been lost. 

My inclination at the moment is to believe it is nothing more than a trashed Grub menu.

However, it is important that you not do anything that is likely to disturb the disc or the date on it, especially since you don't have any recent backup.

Leave it alone. Its probably a simple problem. Don't turn it into a disaster.

> **speed32219 said:**
> ...I did a noob thing, I have not backed up some crucial data for the last 2 months...

Its not really a noob thing. Believe me, I've paid the price. And it wasn't because I didn't know better, it was because I thought I was so smart I didn't need to follow good procedure.

So answer the above and lets see if we can get this solved.

---

### Post by TiredBird on 2009-10-15
I'm in the Central (US) time zone and its past my bedtime. I'm going to get some sleep but I should be available in six hours or so, maybe sooner. Anyway, I'll check back when I wake up. It might be helpful if you were to tell me about your availability also.

---

### Post by oldfred on 2009-10-15
Did you somehow in BIOS reverse the boot of the 160GB dirves They both say bootable but if sdb was not really used its boot may not be valid?

The best way to know what you system is doing and how it is configured is this script:

Boot Info Script 0.32 courtesy of forum member meierfra
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
Instructions
[http://ubuntuforums.org/showpost.php?p=6725571&postcount=3](http://ubuntuforums.org/showpost.php?p=6725571&postcount=3)
cd to directory saved to:
chmod 755 boot_info_script032.sh
sudo ./boot_info_script032.sh
or  as example if on desktop
sudo bash ~/Desktop/boot_info_script*.sh
This will create a RESULTS.txt file in the same directory. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text.

---

### Post by speed32219 on 2009-10-15
TireBird thanks for your help and I am still up, took a break, working on other projects also.  The network is a wired and wireless home, basically front end htpc's with a 8.04 A/V server.  I am upgrading a few of the front ends to support DB and I wanted to put the OS on a USB stick so I could add features/functions and if I screwed it up I could I could just slap in a backup and go right back to screwing more things up. LOL! 

Problem is as I get tired I start trying to do to much and lose concentration which is my downfall, especially after working on something  for 20 hours straight.  Lately been trying to get a Antec Veris basic remote to integrate into Jaunty, works in Intrepid and Hardy after hacking and removing the usbhid drivers, but Jaunty just won't release those darn usbhid drivers which makes the remote useless. So I gave up and then installed Intrepid and that is when I screwed it up, To many hours of no rest and rushing to get it done.  Anyhow, back to the problem at hand, I have a lot of files that I did not back up and they are setting on that darn Drive.

"They are probably not lost, unless you have done a lot of fritzing around"

Nope, no fritzing around, I can not lose that information, even if I have to run external data gathering programs to restore data.  That's why I thought I would come here and kick it around to find the 98-99% solution.  Have a good night sleep, I am still at it here in the Eastern time zone.  I usually stay up to around 5AM and back up between 9 and 10 AM. 

EDIT:  Checked Message:  GRUB

oldfred: "Did you somehow in BIOS reverse the boot of the 160GB dirves "

Yeah, I had thought of that, that would have been an easy one, and I thought I could have done it with the changes I was making on the boots from Bios.  But I went back in and checked and verified that I had the right one.  I noticed too that both drives were bootable.  I at one time had both Ubuntu hardy and I think tiny xp or maybe VB on that drive.  In fact VB I believe is also on the drive that I am having the problems with.
I am going to download that script to take a look at it, always nice to have some additional tools on hand.  Yeah, I am a fly by the seat of your pants type of guy. LOL  My wife calls it reckless.

---

### Post by TiredBird on 2009-10-15
I slept longer than I thought I would. Anyway I'm up now. 

It sounds like like you can be using one machine for internet while working on the broken one - thats great. Still need to know whether that was Grub or Gparted you were seeing. 

Assuming it was Grub, boot the machine with that stick you have. I assume you can get to the command line okay.

---

### Post by speed32219 on 2009-10-15
GRUB.

I am using it now posting this with a Live CD.

---

### Post by TiredBird on 2009-10-15
> **speed32219 said:**
> 
ubuntu@ubuntu:~$ sudo fdisk -l


I assume this was done from a terminal window after booting from the live CD.

> **speed32219 said:**
> 
Disk /dev/sdc: 2051 MB, 2051014656 bytes
255 heads, 63 sectors/track, 249 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000e558f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         231     1855476    b  W95 FAT32
/dev/sdc2             232         249      144585    5  Extended
/dev/sdc5             232         249      144553+  82  Linux swap / Solaris


What is this? It looks like around 2GB of something. You said something about an 8GB flash drive but I can't find anything about this one. Is there another flashdrive plugged into the machine? Is this the Live CD, or what?

> **speed32219 said:**
> 
ubuntu@ubuntu:~$ sudo sfdisk -d
# partition table of /dev/sda
unit: sectors

/dev/sda1 : start=       63, size=312576642, Id= 7, bootable
/dev/sda2 : start=        0, size=        0, Id= 0
/dev/sda3 : start=        0, size=        0, Id= 0
/dev/sda4 : start=        0, size=        0, Id= 0
# partition table of /dev/sdb
unit: sectors

/dev/sdb1 : start=       63, size=312560577, Id= 7, bootable
/dev/sdb2 : start=        0, size=        0, Id= 0
/dev/sdb3 : start=        0, size=        0, Id= 0
/dev/sdb4 : start=        0, size=        0, Id= 0


I guess this is why you think you've lost your partitions. If so, disregard. sfdisk was not designed for large partitions, which you definitely have, and it probably can't read the partition table. Doesn't mean its not there though.

> **speed32219 said:**
> 
ubuntu@ubuntu:~$ sudo parted /dev/sda1 print
Model: Unknown (unknown)
Disk /dev/sda1: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  160GB  160GB  ntfs              

ubuntu@ubuntu:~$ sudo parted /dev/sdb1 print
Model: Unknown (unknown)
Disk /dev/sdb1: 160GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  160GB  160GB  ntfs

What I'm seeing is that you have a computer that has two 160GB hard drives, Each of them formatted with a single partition that is formatted in NTFS. But I'm not seeing where your Ubuntu system is.

---

### Post by TiredBird on 2009-10-15
> **speed32219 said:**
> GRUB.

Was it the Grub menu, a message saying that Grub was starting up, a Grub error message or what?
> **speed32219 said:**
> 
I am using it now posting this with a Live CD.
You are running from the Live CD and getting to the internet that way, do I understand correctly?

---

### Post by speed32219 on 2009-10-15
It is on the sdb1 drive and is probably not showing up due to the disk not being read properly.  It shows --- used and --- available due to maybe partitions missing or resized improperly.  Just grabbing at straws here.

---

### Post by speed32219 on 2009-10-15
Just the word GRUB.  Nothing else. I tried enter and ctrl c with no repsonse.Yesa, I am getting to the internet using live cd on the problem machine.  I now have two systems up and I am posting this using my new test machine.

---

### Post by alphaniner on 2009-10-15
I'm confused.  Are both sda1 and sdb1 supposed to have Windows filesystems?  Is your Ubuntu a wubi installation?  Probably won't help me help you, I just don't like being confused.  Assuming they are supposed to be Windows partitions, do you have any idea why they are different sizes?  And if you could, please use CODE tags if you are going to post terminal output, and maybe separate different commands into their own block.  I go googly-eyed trying to read it.

It's unlikely, but have you considered going at this from a hardware perspective?  I had a SATA cable go bad on me once with absolutely no warning and it caused all manner of hassle.  I would suggest disconnecting the drive that is working properly, and connecting the troublemaker in its place.  Ie. try the 'bad drive' with the power and data cables and mobo port of the 'good drive.'

---

### Post by speed32219 on 2009-10-15
> **alphaniner said:**
> I'm confused.  Are both sda1 and sdb1 supposed to have Windows filesystems?  Is your Ubuntu a wubi installation?  Probably won't help me help you, I just don't like being confused.  Assuming they are supposed to be Windows partitions, do you have any idea why they are different sizes?  And if you could, please use CODE tags if you are going to post terminal output, and maybe separate different commands into their own block.  I go googly-eyed trying to read it.


History

Yes Windows ntfs drive's  Dirve C main OS XP SP2 (with UBUNTU dual boot) and Drive d: (a Data Drive only, no OS but had one installed at one time before I formated and used as a backup Data drive which is why it is proably showing up as a boot dirve also when it is not)

Swapping cables is easily done, but I highly doubt that is the problem.

---

### Post by TiredBird on 2009-10-15
How did you run Gparted? Is it a part of your live CD? Do you have a Gparted Live CD? 

Since I seem to be getting your responses after I've already made my next post, I'm going to make some guesses and ask you to try something that poses no serious risk but might give you a quick fix.

From the live CD terminal window, (command line), activate Grub:

```
sudo Grub

```

From the Grub prompt, (grub>), see if you can find the Grub menu:

```
find /boot/grub/menu.lst
```

if it finds anything, and I hope it does, that should give you something like:

(hdx,y)

where the x and the y are numbers as follows: the x is the hard-drive number minus 1 and the y is the partition number minus 1. (Grub numbers from 0 instead of 1, thats why the minus 1).

If it says it can't find anything, stop, and exit grub:

```
quit
```

You'll have to take a different and longer route.

Otherwise... (my next post - but not until I find out from you what happened.)

---

### Post by speed32219 on 2009-10-15
TiredBird, yes, prior to posting for help I tried that a few times and it always came back with an error 15, file not found.

Also, I ran Gparted and Parted from the live CD.

---

### Post by alphaniner on 2009-10-15
When you have the USB plugged in and boot to it, do you reconfigure the BIOS to make it the primary boot device?

If not, consider the following scenario.  I figure you must be using wubi since you have no Linux partitions.  And while I don't know much about wubi, I don't think it uses GRUB.  My guess is that during the installation to the USB, it installed GRUB to the MBR of the boot HDD, rather than the USB stick.  This would explain why GRUB appears and hangs when the USB is not plugged in.  Of course, it doesn't explain why your primary HDD is malfunctioning... :(

---

### Post by speed32219 on 2009-10-15
alphaniner, Yes if I want to boot from the usb I need to set Bios to recognize the USB drive as the 1st bootable drive.  When I was setting it up to be installed  I had it set as the second drive and my CD ROM as the first bootable drive.  

This is how I got to the install menu of the live CD and when it checked my hardware it found all three drives with other OS's installed.  When I partitioned I selected the 8GB Patriot drive to partition and selected sdc1 for GRUB to write to.  Now, I think when I went to write out GRUB to the USB flash drive I got an error about wrong device (Might have used /dev/hdc1 or something)  and it took me back to the partition editor.  2nd time around I selected sdc1 to write to. It was late and I was in a hurry to get it finished so I could move on to installing Lirc and fixing a usbhid issue.

---

### Post by TiredBird on 2009-10-15
Looks like you're getting plenty of help. I'll check back later and see how you've made out.

---

### Post by speed32219 on 2009-10-15
Your bailing on me?  I can use all the help I can get. LOL!

Need things to try, like should I try and fire up Gparted and try and run a fix?  OR should I use XP to try and fix.  When I installed Ubuntu, GRUB took over but I wonder if the XP boot is still there hidden.

Setting here looking at Gparted it does see the disk.

Partition         Filesystem      Size         Used       Unused      Flags
/dev/sdb1 **! **      ntfs           149.04Gib     ---         ---        boot
unallocated       unallocated    7.84Mib       ---         ---    


So I wonder if I should try and take that 7.84MB of unallocated space and either create a new partition or try and add to the existing.  I wonder if that might correct some of my issues. If Grub was trashed, could it cause the disk to show no disk usage?

---

### Post by ShizzlePDX503 on 2009-10-15
I have been in this same situation a few times myself and I was able to use the Windows XP recovery console to repair the windows boot partitions. This might be an option for you if you have the XP installation CD...

[http://www.windowsnetworking.com/articles_tutorials/wxprcons.html](http://www.windowsnetworking.com/articles_tutorials/wxprcons.html)

not sure if it will affect any linux partitions on that drive or not. If you are not too worried about the linux stuff then this might be an option for you. I will see if I can also find the exact commands that I used to fix this same problem. Though the above link will walk you through everything.

---

### Post by alphaniner on 2009-10-15
GRUB is installed in the MBR, which is part of the first sector of the HDD which also includes your partition table.  IOW, GRUB getting trashed is more likely a symptom than the cause.  One thing you could try is deleting the existing NTFS partition and re-creating it using the whole disk.  If you do it with fdisk, it will only modify the partition table and not the rest of the drive.

I'm still confused how you could have had Ubuntu installed with only two Windows partitions though...

---

### Post by ShizzlePDX503 on 2009-10-15
> **alphaniner said:**
> One thing you could try is deleting the existing NTFS partition and re-creating it using the whole disk.  If you do it with fdisk, it will only modify the partition table and not the rest of the drive.

but he would lose all the data that he is trying to save if he does that.

---

### Post by oldfred on 2009-10-15
If fixing the boot process does not solve the problem, I would try testdisk. It is on most liveCD's or can be downloaded from the repositories. With testdisk you can just analyze or fix disk issues and recover data. 

If you have boot issues still run the script I suggested as it tells which partition grub is looking to boot from and what boot files are in what partitions as well  as UUID, menu.lst and fstab so we can make sure all settings are consistent.

---

### Post by TiredBird on 2009-10-15
It looks like you're getting plenty of help and apparently from people who know what they're talking about. It appears also that you are a lot more knowledgeable about Ubuntu and Linux than I had originally supposed. 

I don't know anything about this media application you are running and its been over a year now since I had a system with Windows on it.

Sorry to bail on you but I don't think I can be of much help.

Good luck.

---

### Post by speed32219 on 2009-10-15
> **alphaniner said:**
> GRUB is installed in the MBR, which is part of the first sector of the HDD which also includes your partition table.  IOW, GRUB getting trashed is more likely a symptom than the cause.  One thing you could try is deleting the existing NTFS partition and re-creating it using the whole disk.  If you do it with fdisk, it will only modify the partition table and not the rest of the drive.

I'm still confused how you could have had Ubuntu installed with only two Windows partitions though...

I do not know why it is not showing an ext3 10-15G partition.  That's partly why I was asking if Grub could affect how it shows partitioning.

---

### Post by alphaniner on 2009-10-15
> **ShizzlePDX503 said:**
> but he would lose all the data that he is trying to save if he does that.

No.  Modifying the partition table *does not touch* the data.  I recently completely wiped and overwrote a table of 5 partitions, but realized it soon enough and lost **nothing**.  Here's the [thread]("http://ubuntuforums.org/showthread.php?t=1280815").

If you have a spare USB stick lying around, I can prove it.  Create a partition using only part of the space and format it with FAT.  Mount and copy some data over.  Unmount.  Delete the partition using fdisk and create a new partition encompassing the entire stick.  Write the changes out.  Mount the new partition (will probably happen automagically in fact), and you will find your data intact.

The moral of the story: the partition table is stored in the first sector of the HDD, and modifying it does not affect the data.

> I do not know why it is not showing an ext3 10-15G partition. That's partly why I was asking if Grub could affect how it shows partitioning.

Well that kinda turns everything on its head.  The absence of an entire partition is something you should have mentioned from the get go.  I'd say your partition table got corrupted.  Check out testdisk.

---

### Post by speed32219 on 2009-10-15
> **oldfred said:**
> If fixing the boot process does not solve the problem, I would try testdisk. It is on most liveCD's or can be downloaded from the repositories. With testdisk you can just analyze or fix disk issues and recover data. 

If you have boot issues still run the script I suggested as it tells which partition grub is looking to boot from and what boot files are in what partitions as well  as UUID, menu.lst and fstab so we can make sure all settings are consistent.

I forgot ot get back to you earlier, I did run that script after I look at it and it could not find the disk.

I have been using the terminal to apt-get a copy of testdisk since late last night, but can't find it even using synaptic on the live CD.

Edit: I just tried to install gparted 0.4.7 which is suppose to have testdisk built into it.  Did not go well with a live CD, all the dependencies are missing.

---

### Post by speed32219 on 2009-10-15
"Well that kinda turns everything on its head. The absence of an entire partition is something you should have mentioned from the get go. I'd say your partition table got corrupted. Check out testdisk."

Sorry about that, I thought I mentioned that I had a dual boot XP and Intrepid even with VB installed (My Bad). I shall be more specific next time.  That is also why I kept mentioning partitions, so now, I guess I gotta figure out how to get testdisk.  I guess I will boot the broken PC with the USB flash instead of the live cd and load it up from that.

I'll let you know how it is coming.

Edit:  Alright, I've booted with the usb I created and install testdisk 6.09.  I selected the sdb2 drive and everything was going oK until near the end when I selected P to list the files.  Error: Can't open File System, File system is damaged.

So I went through it again only this time I selected it to do a Deeper Search.  Now I am confused.
Partition-----------------start-------------------end------------------size
D HPFS - NTFS-------------0 1 1 19455-------------254 63-------------312560577
D HPFS - NTFS-------------0 1 2 19456-------------254 63-------------312576641

With first one highlight message at bottom of screen states NTFS, 160 GB / 149 GiB
With 2nd one highlighted message at bottom of screen states NTFS found using backup sector! 160 GB / 149 GiB

---

### Post by alphaniner on 2009-10-15
> **speed32219 said:**
> Sorry about that, I thought I mentioned that I had a dual boot XP and Intrepid even with VB installed (My Bad). I shall be more specific next time.  That is also why I kept mentioning partitions...

You did mention this, which confused the heck outta me.  And TiredBird was also a bit perplexed, if I may be so bold.  We both asked how you could have had Ubuntu installed with only Windows partitions.  You need to pay closer attention to what the people trying to help you have to say.

Anyway, good luck.

---

### Post by SPr on 2009-10-15
I've read the entire thread and I'm confused too.

<recap>
You had Windows installed on the internal drive and installed Ubuntu on an external USB drive. Is that correct?

After installing Ubuntu on the external USB drive you rebooted and nothing would boot? Is that correct?

You played with gparted which told you that the NTFS partition is corrupted. Is that correct?
</recap>

Rather than re-read the whole thread did you ever tell us to which drive Grub was installed? It should have been installed to the USB drive.

If you put Grub on the internal HDD that will account for the warnings about the NTFS partition being corrupted. It can be fixed but first let us know if my assumptions are correct or not. After we know what you have done to your PC I'm certain someone here will be able to help you fix it.

Get Windows booting again and then start fixing the Ubuntu install. If the Ubuntu install contains important data it can be read from within Windows (with the right tool Windows can read ext3).

First and foremost. Give us the information that is as asked of you in a straight-forward manner and as concisely, clearly and accurately as possible.

---

### Post by alphaniner on 2009-10-15
> I've read the entire thread and I'm confused too.

<recap>
...

Most of this I think I can now answer.

He had Windows and Ubuntu installed to one HDD, and a single NTFS partition on a second HDD.  GRUB was his bootloader, installed to the MBR of the first HDD.

He installed Ubuntu to a USB drive and a copy of GRUB was installed there.  When configured to boot from the USB drive, GRUB works and the system boots.  When re-configured to boot from the HDD (the previous configuration), GRUB craps out.  Also, the partitions on the 'master' HDD are borked.  He should have an NTFS partition and an ext3 partition (and presumably a swap partition), but he only has an NTFS partition that is somehow corrupted; it will not mount and spits errors when he tries to look at it with gParted.  He will not be able to get his Windows install up until he fixes the partition issues, assuming that is all that's amiss.

Right now he is trying to get testdisk up and running to fix the partitions.

---

### Post by speed32219 on 2009-10-15
SPr, that's what I said. kinda in a long way around.

alphaniner, that is what I wanted to post the first time. Thanks.

OK, here is what testdisk spit out.

Alright, I've booted with the usb I created and install testdisk 6.09. I selected the sdb2 drive and everything was going oK until near the end when I selected P to list the files. Error: Can't open File System, File system is damaged.

So I went through it again only this time I selected it to do a Deeper Search. Now I am confused.
Partition-----------------start-------------------end------------------size
D HPFS - NTFS-------------0 1 1 19455-------------254 63-------------312560577
D HPFS - NTFS-------------0 1 2 19456-------------254 63-------------312576641

With first one highlight message at bottom of screen states NTFS, 160 GB / 149 GiB
With 2nd one highlighted message at bottom of screen states NTFS found using backup sector! 160 GB / 149 GiB 

Please note that I did this twice, the first time the first entry was in green with a P instead of the D.  The second time around they are both in white with D's in front.

This is where I am now

---

### Post by alphaniner on 2009-10-15
Well, that certainly isn't right if you had an ext3 partition on that drive.  The man page for testdisk sucks hard, but according to the web page 'D' stands for Deleted and 'P' stands for Primary.  Did you go through the [instructions]("http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step")?  I dunno, you may need to try another application.  The time I told you about when my SATA cable went bad, I managed to do some real damage before I figured it out.  I had to use a commercial product to recover my data, but I was able to recover 99% of it.  Don't remember the name though. :confused:

Edit: I've never used testdisk before, so you should wait for some advice from someone who is familiar with it!

---

### Post by speed32219 on 2009-10-15
Thank you for the help though.  While I was awaiting for a response, I just checked and the bottom on had turned green with a P.  I don't know what the heck is going on either.  It's nice to have someone as a soudning board and to share.

Thank you everyone.  Guess I will try and install tiny XP on a usb card next to see if I can get to the drive, or use some of the available data recovery tools out there.  I just can not go any further until I recover a few directories including my mail.

---

### Post by alphaniner on 2009-10-15
Did you go through the instructions, including running a 'Deeper Search'?

---

### Post by speed32219 on 2009-10-15
Yes, that was my post above.  And if I highlight one of the above stings from the search and press P (Display files) I get an error, file system corrupt.  IT just isn't working, I just loaded up Tiny Xp to create a usb disk but i9t had some recovery tools on it so I selected a package called spinrite and it looks to be rebuilding right now.  It is at 38% complete.  I will let you know how it is doing, probably going to take another hour.

---

### Post by alphaniner on 2009-10-15
By 'rebuilding' do you mean it is writing to or modifying the contents of the HDD?  If so I hope it works, because you may not get any second chances.

---

### Post by speed32219 on 2009-10-15
Ah, I think it is just processing the data to see if it can be recovered. 
Heck, that's why I posted here first before doing something else to add adventure to my life.  Just more challenges I guess, we'll see.  I think I may run it on both drives to see the differences.

---

### Post by alphaniner on 2009-10-15
Have you looked at [this thread]("http://ubuntuforums.org/showthread.php?t=1290215")?  It seems similar to your situation but there's a lot more people posting there.

Edit: I'm off for the day and probably won't return until tomorrow.  Good luck.

---

### Post by speed32219 on 2009-10-16
Yes, I started to read that thread but I realized that my problem was very close but not the same.  I didn't want to post in there and hijack someones thread so I started this one.

After much searching, it looks like the best solution to fix this problem is going to be with chkdsk, since this is an ntfs file system. I am now trying to do just that, if I can find my original XP disk.

Posted in there this morning, Chkdsk wouldn't even start before notifying me that the dirve had to many errors,  and I am back here still trying.  Kinda cleaned up your synopsis of my problem with a few selected cmd outputs to simplify my problem. :D

---

### Post by speed32219 on 2009-10-19
Alphaniner, thanks for the input.  After reading about not destroying the data you posted I went ahead and deleted the MBR and partitions.  Rebooted and used testdisk to create a new MBR and write it out.  Rebooted and then was able to create a partition (NTFS) and finally found my data and made backups.  

I need to do some research on this subject, it is one I do not understand and I am alsways afraid of losing my data.

I think I will take your suggestions and start playing around with a 2 GB USB Flash and setup some test paritions.

Anyway, I am marking this as closed.

I will probably open a new post on how to get my Ubuntu partition back.  I have found it as far as an unidentiified partition, but when I use testdisk to try and create the partition type, I do not see a linux type of partition.  It lists linux raid and xenix, out of about 20 types, but no unbuntu or plain generic ext2/3 type's.  Maybe I should use parted or gparted for this part, but good hte news is, I have my lost Data Back and stored on another dirve.

---

