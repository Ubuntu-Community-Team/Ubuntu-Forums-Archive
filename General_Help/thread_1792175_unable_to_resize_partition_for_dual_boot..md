---
title: "unable to resize partition for dual boot."
date: 2011-06-27
forum: General Help
---

### Post by Matrix01 on 2011-06-27
I use HP mini, and have Gparted and Ubuntu in USB.

I opened up Gparted, and 

selected the largest size of memory of partition, and 
selected re-sizing from drop down menu.

re-sizing is disabled on tab.

this's the web that I got instructions from.
[http://members.iinet.net.au/~herman546/p22.html]("http://members.iinet.net.au/%7Eherman546/p22.html")

any help?

---

### Post by drs305 on 2011-06-27
I wrote the following guide a while back that explains how to take space from Windows and give it to Ubuntu:
[http://ubuntuforums.org/showthread.php?t=1219270]("http://ubuntuforums.org/showthread.php?t=1219270")
At the bottom of that page is a link to a great page by srs5694 that also deals with this.

One common reason that partitions can't be resized is because the partitions are still mounted. This includes the swap partition, which is mounted even when using the LiveCD. It must be unmounted before resizing operations can be performed.

---

### Post by Matrix01 on 2011-06-27
how do u unmount the partition?

---

### Post by Bucky Ball on 2011-06-27
> **Matrix01 said:**
> how do u unmount the partition?

Boot from LiveCD, open Gparted when at the desktop, right click partitions and unmount. You can't unmount them on a system running from the hard drive. I generally resize Windows partitions in Windows with MS software. That has been most reliable for me.

IMPORTANT: De-fragment your Windows partition(s) before resizing them! Do it a couple of times if possible. This will give you the closest idea of how much is there and how much you have to shrink.

No doubt there is this info and more in drs305's how to ...

---

### Post by drs305 on 2011-06-27
> **Matrix01 said:**
> how do u unmount the partition?


In Gparted, mounted partitions are indicated with a 'key' icon next to them. Select the partition, then either right click, Unmount, or from the top menu Partition, Unmount.

---

### Post by Matrix01 on 2011-06-28
I opened gparted...
there's warning sign, "!" is in a triangle...in sd2

i clicked on sd2
sd2 is Not mounted....
and resizing is disabled on tab.

file system : ntfs.
status: not mounted.

and..
cluster accounting failed at 197243 (0 x 30276)  extra cluster in $ Bitmap...
what is this about?

---

### Post by Bucky Ball on 2011-06-28
What's on SDA2? (not sd2 - that wouldn't exist). Is that where Windows is? Take my previous advice; defrag that before shrinking or tweaking those partitions.

Backup any Windows stuff you want to keep before stuffing around too much from here I would advise ... ;)

---

### Post by Mark Phelps on 2011-06-28
If your HP Mini is running Win7, then use the Win7 Disk Management utility to shrink the Win7 OS partition, do NOT use GParted or the Ubuntu installer.

If it's running Win XP, you should be OK using GParted or the Ubuntu installer.

---

### Post by Matrix01 on 2011-06-28
someone replied to my thread in "beginner's talk" for a while ago....
they said some people got problems after using W' disk management.



Iced Blended Vanilla Crème Ubuntu
 
Join Date: Mar 2010
Location: Woonsocket, RI USA
Beans: 2,749
    
Re: how to partition with window disk management?
Do not use Windows' Disk Management tool to create new partitions for Linux!!!!!

This program has the unfortunate tendency to turn partitions into "dynamic disks" (aka Logical Disk Manager, or LDM, volumes) with little or no warning given to the user. The trouble is that LDM is a Microsoft-only technology. Although Linux has some basic LDM support, you can't modify LDM volumes in Linux, and installing Linux to an LDM volume is difficult or impossible. (I've not looked into it in enough depth to know which.) This problem seems to be most likely to arise when you raise the number of partitions on the disk above 4, but I don't know the exact trigger conditions -- if that always happens, or only if all the original partitions were primaries, or whatever.

There have been many threads here from people who've fallen into this trap. Getting out of it requires either a complete disk backup/restore operation or running a partitioning tool that can do the reverse conversion. At least two Windows programs are supposed to be able to do this, but I don't know how well they work or how safe or reliable this reverse conversion is. It's best to avoid the trap rather than rely on such tools.
__________________
If I've suggested a solution to a problem and you're not the original poster, do not try my solution! Problems can seem similar but be different, and a good solution to one problem can make another worse. Post a new thread with your problem details.
srs5694 is online now Report Post       Reply With Quote

---

### Post by Mark Phelps on 2011-06-29
Matrix01: THAT problem, of Dynamic Disks, only happens if you try to use Win7 Disk Management to CREATE partitions. 

My advice has always been:
1) Use Win7 Disk Management to SHRINK Win7 OS partitions -- leaving unallocated space
2) Use Linux utilities to create Linux filesystem partitions (NOT Win7 Disk Management).

---

### Post by Matrix01 on 2011-07-05
I did defrag for a while ago,
so
i am going back to ubuntu, and Gparted,
and try to resize disk.

---

### Post by oldfred on 2011-07-05
If sda2 is a NTFS partition, gparted will not mount it or use it if it sees a problem that needs chkdsk. Sometimes window will still load, but Linux seems more sensitive to NTFS issues.

Try running chkdsk from a window repair CD.

Vista/7 CHKDSK
chkdsk [drive] /f /r
chkdsk C: /r
/f : Fixes errors on the disk.
/r : Locates bad sectors and recovers readable information.
Note If you specify the /r option, the /p option is implied. When you specify the chkdsk command without arguments, the command checks the current drive with no options in effect. Rerun until no errors.
[http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true](http://www.microsoft.com/resources/documentation/windows/xp/all/proddocs/en-us/chkdsk.mspx?mfr=true)

Thread with this and other repair suggestions
[http://ubuntuforums.org/showthread.php?t=1393848](http://ubuntuforums.org/showthread.php?t=1393848)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by Matrix01 on 2011-07-05
i opened up win7 (starter) disk management.

it is.....C drive is  NTFS file system....i guess that this partition is sda2 in Gparted.

---

### Post by Matrix01 on 2011-07-07
I have win7 starter,

how do i get window repair CD?

---

### Post by oldfred on 2011-07-07
You should have a repair CD or Ubuntu LiveCD or USB for every system you have installed. Also a good idea to have some other repair type liveCDs.

Make your own recoveryCD:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)

[http://partedmagic.com/](http://partedmagic.com/)
[http://gparted.sourceforge.net/faq.php](http://gparted.sourceforge.net/faq.php)
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)
[http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk](http://www.supergrubdisk.org/wiki/AutoSuperGrubDisk)
Howto: Easy GRUB Bootloader Repair Windows,unetbootin, Supergrub 2008
[http://ubuntuforums.org/showthread.php?t=690912](http://ubuntuforums.org/showthread.php?t=690912)
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by darkomano on 2011-07-08
Capital letters: 
[COLOR=lime]DO NOT USE ANYTHING BUT WINDOWS TOOLS TO MANIPULATE WINDOWS PARTITIONS[/COLOR] !
 
Windows puts a partition ID on Windows partitions - it is overwritten using external tools.
This ID is used and checked on boot and mount.
 
A good method for resizing a Windows partition would be to either use defragmenter that comes with Windows or another good tool to reorder files on disk moving them to the beginning of the partition. Then use Windows Disk Management to resize the partition.
 
The free space later can be managed by Ubuntu.

---

