---
title: "setting up Win 7 for dual boot?"
date: 2011-10-15
forum: General Help
---

### Post by garyed on 2011-10-15
I've got my new laptop with Windows 7 HP installed.
Since the 11.10 live CD works O.K. I'm ready to install it & dual boot.
I'm familiar with dual booting with XP but I've heard that Windows 7 is a lot more touchy about partitioning. I'd also like to still be able to use the Windows recovery partition if I ever need to reinstall Windows. Any ideas on what to do or not do before I start would be appreciated.

---

### Post by Ceiber Boy on 2011-10-15
> **garyed said:**
> I've got my new laptop with Windows 7 HP installed.
Since the 11.10 live CD works O.K. I'm ready to install it & dual boot.
I'm familiar with dual booting with XP but I've heard that Windows 7 is a lot more touchy about partitioning. I'd also like to still be able to use the Windows recovery partition if I ever need to reinstall Windows. Any ideas on what to do or not do before I start would be appreciated.

If it was my machine I would boot from a live cd and use the program dd to clone the HDD to external storage, HDD server or whatever. This acts as a safety net because if things go wrong you will be able to restore your computer FULLY to the point before you started making any changes. Windows recovery disks become redundant if you have a full clone of your HDD which is what dd will provide for you.

Windows 7 has the ability to resize it's resident partition, so make a free partition with windows 7 inwhich to install ubuntu, then boot from your ubuntu cd and install th os into the space you've made.

---

### Post by oldfred on 2011-10-15
Do not make partitions with the Windows 7 MMC, just use it to shrink and make unallocated space.

Most Windows 7 systes use all 4 primary partitions.

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)
The Hedge show graphically how to delete & create partitions:
[http://ubuntuforums.org/showthread.php?t=1713649](http://ubuntuforums.org/showthread.php?t=1713649)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by HarcourtMarketing on 2011-10-15
Using just one hard disk, try this.  And assuming 200 gig.

Use Win7 defrag and that disk defrag program from ccleaner maker site. Pifiform....? I forget. I'd do each twice one after another.

Live boot gpart, resize down to around 60gig Win7, to the right resize/format ntfs to 100gig, to the right resize/format ext3 to 38gig, to right format swap to about 2gig. (+/-) for your hdd.

Label each one also, Win7, BackUp, Linux, Swap.

Reboot Win7, play around in explorer a bit, look at it in admin tools ect.

Reboot Win 7 again, play around again.

Boot live then install Linux in it's partition, choose to format, (as ext3 may or not be best for that distro (?)) Just did it with gpart to get Win7 used to not 'seeing' it and freaking out next time it boots.... seems to have helped in the past.

But, what seems important mostly is defrag, (guess 'em files get strewn all over the disk area) and re-booting a couple times.

Linux likes and should be re-booted after gpart prior to install also.

Have done with one, two and three hdds'. (One hdd on a laptop)

Now have one hdd just for XP/7/2gig pagefile/backup, then 4 ntfs partitions as backups on #2 hdd, then #3 as ntfs/ntfs/ext3/swap.

All are labeled, Win and Linux reads all labels. Makes it easier.

Seems ext/swap as far right as possible works best, sata 1, sata 2, sata 3.....ect. So, sata 1, 2, 3, ect. which ever is 'last' gets ntfs/ntfs/ext3/swap. Works every-time and all re-installs are a snap. (Mainly due to 'Fix MBR' in Live Linux ease.)

Win7 with 3 or 4 different distros dual boot with 1 or 3 hdd have worked good.

Good thing is you can save all your stuff in ntfs backups and access through win or x. Or as I do, one VB file in a backup for my asp.net site coding and backups of it elsewhere. Keeps it safe, either Win or Linux VB works well with it.

For me it's like 98.9% Linux usage ( I still like Battlefield online ), but do I boot an rpm or deb distro today...Ummmmmmmmm

---

### Post by garyed on 2011-10-15
Thanks for all the help.
I've been away from Windows so long that I feel like a novice whenever I get near it. I never got past XP & ever since I started with Ubuntu I don't use Windows much at all. I'm not sure I'm going to be happy with 11.10 from all that I'm hearing but I wasn't happy with Grub2 as opposed to legacy Grub until I got the hang of it either.

---

### Post by garyed on 2011-10-16
Well I went to windows disk manager to shrink the partition from roughly 220 down to 110 gig which is the most it would allow.
The funny thing is that it shows four primary partitions already in use. 

1 - (System,Active partition) 199 mb
2 - C (boot,page file,crash dump partition)110 gig after shrinking
3 - D drive (Recovery partition) 13.6 gig
4 - (HP tools) 103 mb  FAT32 

I haven't tried Gparted yet butt I'm assuming I'm going to have to delete one of the primary partitions to be able to install Ubuntu.
Does that sound correct?

---

### Post by oldfred on 2011-10-16
See post #3. 

You can backup HP tools as it is tiny. I understand you can also download it again from HP. 

Some make the DVD's and just save that in case they ever want to sell computer as it just restores to as purchased. Then really save backups after all the housecleaning & updates. Then they also or delete the recovery. But if you ever need recovery you may have to pay HP for new disks. Some said they will send it free others seem to have had to pay.

---

### Post by garyed on 2011-10-16
I went ahead & made the recovery disks so I assume no matter what I do I can put things back to the factory state again if needed.
I reread post # 3 & see others have run into the same problem but I was thinking the same thing about deleting the HP tools partition & then using it for Ubuntu's primary partition.
Thanks again

---

### Post by garyed on 2011-10-17
With a little help from you guys everything worked out perfectly.
I just have about 103MB unallocated partition wasted that I may decide to use for something someday. Here are the steps I took just in case someone else is going through the same thing I was.

1 - I booted into Windows & used their disk manager to shrink the large partition leaving the rest unallocated & then deleted the small fourth partition leaving it unallocated & then shut down.

2 - I booted from a Gparted live CD & made a new ext4 extended partition out of the large unallocated space but left 2 gig for a swap partition. 

3 - made a new swap partition out of the 2 gig.

4 - Shut down & rebooted with 11.10 live CD & chose Install & when the options for how to install came up I chose "other" which is the same as "manual" on older versions of Ubuntu. 

5 - Set the ext4 partition to "/" as a mount point & the other swap partition was already set so that was it.

Everything installed like a breeze.
I didn't create a home partition which I probably should have but I might add it later but that's for another thread.

I would definitely recommend to make a complete system backup & system recovery disk before doing anything. Once I did that my fear was gone & it made things a whole lot easier. I think I'm going to mark this thread as solved & thanks again to all for the help.

---

