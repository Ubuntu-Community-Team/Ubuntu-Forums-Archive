---
title: "Windows Boot/BCD error"
date: 2011-10-05
forum: General Help
---

### Post by Swazilli on 2011-10-05
So I installed Ubuntu on one hard drive with Windows 7. When I use grub to boot Ubuntu, everything works fine. When I try to boot Windows 7 I get an error talking about "Boot/BCD". The Windows partition is intact as I can access its files from Ubuntu.

Now, I have searched this issue before. It recommended I use my Install DVD. I tried that. However, when I select repair option it says that the version of Windows is incompatible with the DVD. However this is the install DVD I used. I borrowed a coworker's install DVD (mine is x64, his is x86). Still no luck. Anyone have any suggestions?

---

### Post by ubun2geek on 2011-10-05
[http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/](http://www.arsgeek.com/2008/01/15/how-to-fix-your-windows-mbr-with-an-ubuntu-livecd/)

---

### Post by ubun2geek on 2011-10-05
That will fix the MBR. Hope it helps!

---

### Post by Swazilli on 2011-10-06
Hey, Thank you for the quick reply. Several more questions. I am on Ubuntu 11.04. How would I enable the Universal Repository?

Also when I run fdisk it warns me about: "GPT (GUID Partition Table)". That is how I partitioned my hard drive. So I can't really see the right /dev/sda. However, if I open up disk utility, I can find it. Can I just use the disc utility?

---

### Post by Swazilli on 2011-10-06
Sorry for the double post. I managed to install ms-sys. I ran it and it made my ntfs system become Unknown. I could no longer access my Windows files! Luckily I managed to fix it using this:

[http://www.absolutelytech.com/2010/09/23/solved-unknown-filesystem-in-gparted-in-ubuntu/](http://www.absolutelytech.com/2010/09/23/solved-unknown-filesystem-in-gparted-in-ubuntu/)

So I can still see my files (whew). But I can not boot into it. On another side, I no longer have a Boot/BCD error. Now I just get an "No active partition table" error

---

### Post by ubun2geek on 2011-10-06
I am sorry to hear that. I have less experience than most here. Maybe anewguy or haqing could help us. I'll keep looking though. Don't give up! BTW, if you haven't yet, you might want to back everything up before you try more stuff.

---

### Post by Mark Phelps on 2011-10-06
That last error indicates that the partition table you your drive that previously held Win7 is corrupted now.

Did you allow the Ubuntu installer to shrink Win7 in a side-by-side install?  IF so, that's most likely what corrupted Win7, rendering it unbootable.  Have tried to warn people about this, but many do not bother to check here BEFORE doing the dual-boot setup.

Also, as to the version difference, did you upgrade to Win7 SP1 since you originally installed Win7? If so, that would explain the version difference because the system files got changed quite a bit for SP1.

What you could try (it MIGHT work) is going to the link below, downloading and burning the proper Win7 Repair CD image, and seeing if that works:

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Note: These images are NOT free, anymore.  Had you bothered to check here BEFORE you did the Ubuntu install, I would have advised you to use the Win7 Backup feature to create and burn your own FREE Win7 Repair CD -- and if you have upgraded using Service Pack 1, that version would have been written to the CD.

---

### Post by Swazilli on 2011-10-06
> **ubun2geek said:**
> I am sorry to hear that. I have less experience than most here. Maybe anewguy or haqing could help us. I'll keep looking though. Don't give up! BTW, if you haven't yet, you might want to back everything up before you try more stuff.

Oh Yes. I am not going to risk it again. All files are now backed up on an external drive. 

> Did you allow the Ubuntu installer to shrink Win7 in a side-by-side installUnless it shrunk it automatically without telling me then no. I made room for Ubuntu using Windows 7


>  did you upgrade to Win7 SP1Yes. This is probably the issue. I am going to ask aound for a Windows 7 x64 SP1 disc and then post my results. Would the standard procedure to fixing my error be using bootrec.exe?

Thank you for pointing me in the right direction.

---

### Post by viperdvman on 2011-10-06
If you're shrinking ANY partition that contains ANY Windows install, make sure there is no data occupying the last XX gigabytes of space on that partition. A program like Defraggler [http://www.piriform.com/defraggler](http://www.piriform.com/defraggler) (do not replace your WIndows Defrag with it unless you absolutely want to) is a good program that displays a fairly detailed map of your hard drive, moreso than Windows XP's defrag does. As long as there is nothing on, say, the last 20GB of your hard drive, you should be able to shrink it no problem. Just make sure that after you shrink the partition, that you run a CHKDSK (whether in WIndows XP or Windows Vista/7) if it doesn't do that automatically.

---

### Post by Swazilli on 2011-10-10
Here is an update:

I tried accessing the repair console using a Windows 7 SP1 disc. I still get the repair is not compatible with the current Windows installation. Perhaps this has something to do with the fact that my system is GPT partitioned? 

I then tried to reinstall MBR using various tools like "**[Rescatux]("http://www.supergrubdisk.org/rescatux/")" and "[Boot Repair Tool]("https://help.ubuntu.com/community/Boot-Repair")"**. I tried on both the Ubuntu Partition and the Windows Partition. 

As a result I have corrupted grub. I can now only boot ubuntu using a super grub disc. I have no clue on how to fix this.

I also tried playing around with the boot flags (alternate between ubuntu and windows). No effect. I now get either one of these two errors:

1) I boot my computer and all it says is "MBR1:"
2) If I use super grub disc and then use grub to access Window's files I get a "Operating System Not Found" and "Missing operating system" error. The files have remained intact.

I have no idea how to proceed from here. Any suggestions are highly appreciated.

---

