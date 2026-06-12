---
title: "Dual Booting 11.04 and Win7 goes wrong"
date: 2011-07-14
forum: General Help
---

### Post by newworldforce on 2011-07-14
Got a HP dv6-3019wm laptop yesterday and my attempt to dual boot has gone up in flames.
I first followed the tutorial [http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/](http://www.linuxbsdos.com/2011/05/22/how-to-dual-boot-windows-7-and-ubuntu-11-04/)
I might have gone wrong by accidentally making the hard disk 'dynamic' after shrinking the windows partition. Upon booting the computer up after the 11.04 installation, Win7 gave me a 0xc0000225 error.  The built in hard drive recovery didn't work and neither have multiple win7 64b recovery disks I have downloaded.  A gparted live cd wouldn't boot.  On attempting to reinstall 11.04 (so I can just get rid of win7), the installation freezes when it tries to recognize the state of my hard drive.

I've basically turned to dban, but that won't even work.  The latest version gives me an error of "no configuration file found" and 1.0.7 give me "non-fatal error", even when I attempt to auto-nuke.

Am I out a hard drive?

---

### Post by seawolf167 on 2011-07-14
Welcome to the forums!

Can you boot off the Ubuntu LiveCD? A LiveCD environment doesn't need a hard drive to run, so if you can't boot off it I suspect you have at least one other problem (is booting from a cd enabled in BIOS?)

---

### Post by newworldforce on 2011-07-14
Yes, I have been able to boot the live cd, just not install again.

---

### Post by oldfred on 2011-07-14
If you attempted to create more than 4 partitions in windows it converts to dynamic and you officially per Microsoft cannot convert back without a full backup & reinstall.

Posts by oldfred & srs5694
[http://ubuntuforums.org/showthread.php?t=1705481](http://ubuntuforums.org/showthread.php?t=1705481)
SFS converting:
[http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html](http://www.sevenforums.com/tutorials/26829-convert-dynamic-disk-basic-disk.html)
Dynamic volume is a Microsoft proprietary format developed together with Veritas (now acquired by Symantec) for logical volumes.
You can use a third-party tool, such as Partition Wizard 4.2. to convert a convert a dynamic disk to a basic disk without having to delete or format them.
The Partition Wizard software for Windows is supposed to be able to convert dynamic disks to regular partitions without data loss, so it may be what you need to get around this problem; however, I've never used it and so I can't be sure it will work.

One user used these two:
MiniTool Partition Wizard Professional Edition 5.2 to convert without loss of data the disk from dynamic disk to a basic disk.
also used Partition Wizard to set an existing partition logical instead of primary
[http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html](http://www.partitionwizard.com/convertpartition/convert-to-basic-disk.html)
Converted from dynamic with MiniTool, & repaired windows
[http://ubuntuforums.org/showthread.php?t=1779529](http://ubuntuforums.org/showthread.php?t=1779529)

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a windows repair CD.
HP tools partition discussion:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)
Shrinking a Windows 7 partition is best done in Windows. But do not create new partitions.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by seawolf167 on 2011-07-14
> **newworldforce said:**
> Yes, I have been able to boot the live cd, just not install again.

You can't select to manually partition and delete then reformat any existing partitions at all?

---

### Post by newworldforce on 2011-07-14
> **seawolf167 said:**
> You can't select to manually partition and delete then reformat any existing partitions at all?
I can't get to that part in the installation process.

---

### Post by oldfred on 2011-07-14
Gparted & the installer will not work with dynamic partitions and they are Windows only. They are a logical volume like Linux's LVM and gparted should not be used on LVM's either.

---

### Post by newworldforce on 2011-07-15
In the end, I'm just using 11.04.  I found Disk Utility on the live cd and just reformatted the drive.

---

