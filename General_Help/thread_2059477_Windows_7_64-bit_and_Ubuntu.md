---
title: "Windows 7 64-bit and Ubuntu"
date: 2012-09-18
forum: General Help
---

### Post by CWBillow on 2012-09-18
[SIZE=2]I have 2 hard drives, one dedicated to Windows 7, and the other set up with 4 partitions.

I saw something about Ubuntu not being able to be installed if there are four partitions.

Would I need to get rid of one of the 4, or make room on my Windows platter, or...?

Also, will Ubuntu play well with Windows 64-bit?  Should I use 84-bit Ubuntu if there is such an animal?

And then, compatibility:  What do I do about all my MS Office documents? Are they readily readable by Ubuntu, or will I need to convert them?  I have to still use Word for projects I am working on, so what will this do or mean?

Regards,
Chuck Billow
[/SIZE]

---

### Post by Mark Phelps on 2012-09-18
> **CWBillow said:**
> [SIZE=2]I have 2 hard drives, one dedicated to Windows 7, and the other set up with 4 partitions.

I saw something about Ubuntu not being able to be installed if there are four partitions.

Would I need to get rid of one of the 4, or make room on my Windows platter, or...?
The 4 partition limit is true -- 4 Primary partitions or three Primary and one Extended.  You would need to (1) get rid of one to make room, (2) Create an extended partition in its place, (3) install Ubuntu inside the extended partition.

> Also, will Ubuntu play well with Windows 64-bit? 
Don't know what you mean.  These are independent, totally different OSs. They don't work together at all.
>  Should I use 84-bit Ubuntu if there is such an animal? Not aware of 84-bit anything.

> And then, compatibility:  What do I do about all my MS Office documents? Are they readily readable by Ubuntu, or will I need to convert them?  I have to still use Word for projects I am working on, so what will this do or mean?
MS Office works best (big surprise!) in MS Windows.  If you need to rely on MS Office on a daily basis, then you need to keep MS Windows around for that.  Some folks may mention Wine or its variants, but it doesn't work well with Office 2010. Plus, Word 2010 defaults to .docx format files -- which Linux apps don't handle well.

---

### Post by oldfred on 2012-09-18
With two drives you do want to keep Windows on one drive and Ubuntu on the other. The automatic install options do not really do that, but even if you specify the second drive, it will install the grub2 boot loader to the MBR of the sda or usually the Windows drive.

Some suggest physically disconnecting the Windows drive to guarantee no interference.

If you do the manual install and choose the second drive as the location to install the grub2 boot loader you can install without disconnecting drive. See png on last link below. Generally is should be /dev/sdb and the description of the drive, do not use partitions like sdb1 or sdb2. 

 Install to external drive 11.04. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

---

