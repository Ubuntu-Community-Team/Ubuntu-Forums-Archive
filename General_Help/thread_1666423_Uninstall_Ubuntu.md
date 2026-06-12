---
title: "Uninstall Ubuntu"
date: 2011-01-13
forum: General Help
---

### Post by bradRNstyle on 2011-01-13
All my computers are Ubuntu, I love it.  However, there is one person in my house who does not want it anymore.  How do I uninstall Ubuntu?  The computer is a dual-boot (W7 and Ubuntu), I need to uninstall Ubuntu and rid the computer of the partition, making the whole hard drive available to W7.  Is there a good way to do this other than reinstalling W7?

Thanks.

Sincerely,
Sad person who has to uninstall Ubuntu =(

---

### Post by Primefalcon on 2011-01-13
simply load up a live disk of ubuntu and delete your ubuntu partition and resize the windows partition to take up all the space, what you'll then need to do is boot from the windows disk and then run the command fixmbr (which tells the computer to look to windows for the bootloader)

---

### Post by bradRNstyle on 2011-01-13
Thanks, I'll look into that.  But when I use the command "fixmbr" from the Windows 7 command line, I get an error saying its not recognized as an internal or external command.  If before I uninstall Ubuntu, I set the default boot to the W7 loader, will it remain as such after the uninstall?

---

### Post by wilee-nilee on 2011-01-13
Do yourself a favor and restore the W7 bootloader first, using a recovery disc , here is a link to the disc and the **correct command**
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Notice this W7 forum link for a visual of the path to the command line on the recovery disc.


Then after you have W7 booting on its own remove Ubuntu with the disk manager in windows. You should be able to expand the W7 into the unallocated space with its disk manager. Gparted can be used for the removal of Ubuntu as well just turn off the swap before you try.

---

### Post by bradRNstyle on 2011-01-13
> **wilee-nilee said:**
> Do yourself a favor and restore the W7 bootloader first, using a recovery disc , here is a link to the disc and the **correct command**
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

1) Boot with your Vista/Windows 7 installation disk. Hit <Enter> at the language selection prompt then hit <R> for Repair to get to the Repair section. 
2) Select the command prompt (console) and type in the following commands:
BootRec.exe /fixmbr 
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
Notice this W7 forum link for a visual of the path to the command line on the recovery disc.


Then after you have W7 booting on its own remove Ubuntu with the disk manager in windows. You should be able to expand the W7 into the unallocated space with its disk manager. Gparted can be used for the removal of Ubuntu as well just turn off the swap before you try.


Thanks!  That fixed my MBR issue.  But where in windows 7 do I find the second part, about resizing the windows partition.

---

### Post by wilee-nilee on 2011-01-13
> **bradRNstyle said:**
> Thanks!  That fixed my MBR issue.  But where in windows 7 do I find the second part, about resizing the windows partition.

I W7 admin type disk in the start and choose create and format hard disk partitions.

---

### Post by bryanfblareunion on 2011-01-13
I think the real question here is: WHY WOULD ANYONE WANT TO UNINSTALL UBUNTU???

---

### Post by wilee-nilee on 2011-01-13
> **bryanfblareunion said:**
> I think the real question here is: WHY WOULD ANYONE WANT TO UNINSTALL UBUNTU???

Ding ding you get the stupid question of the month award.

The answer is that the rest of the world does not live in your reality as you.

---

