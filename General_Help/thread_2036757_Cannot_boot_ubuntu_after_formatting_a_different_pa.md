---
title: "Cannot boot ubuntu after formatting a different partition."
date: 2012-08-02
forum: General Help
---

### Post by xioSlayer on 2012-08-02
I have ubuntu server dual booted with windows 7.  I reformatted my windows 7 partition to reinstall and as expected it overwrote Grub.  I used a ubuntu desktop live cd to run boot-repair.  

This restored GRUB, but now ubuntu won't boot.  It says "**the disk drive for /home is not ready yet or not present, continue to wait, or press S to skip mounting or M for manual recovery.**"

S brings me to my login screen (i have the gui running on the server), but the background is black and none of the features work, I cannot log in.

How can I fix this?  Any help would be much appreciated. thank you.


EDIT:  Here is my boot-repair log:  [paste.ubuntu.com/1126013]("paste.ubuntu.com/1126013") and GRUB has two entries for windows 7 now (sda1 and 2).  They both succesfully boot into windows?  Why are there two now and how do I remove one?

---

### Post by oldfred on 2012-08-02
You do not show a sda6 which your fstab says was /home when originally installed. It does look like you have some space in your extended partition that may have been an sda6?

Windows 7 often has a 100MB boot/repair (hidden) partitio and then a main (c: drive) partition. Usually 2 of the three required boot files not not in the main partition, but if you repair or reinstall it may then have them. Many Windows system also have another bootable partition that is just the recovery partition.

Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7 (with 7 the first two files are usually in a separate 100MB boot partition)
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

Probably the best way to remove the extra entry if you do not want it.

HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)
[http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html](http://www.ubuntugeek.com/grub-customizer-2-2-released-and-installation-instructions-included.html)
The Grub 2 Guide - drs305 also link to grub customizer
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)


You may be able to recover old /home with testdisk.

[https://help.ubuntu.com/community/DataRecovery#Lost%20Partition](https://help.ubuntu.com/community/DataRecovery#Lost%20Partition)

Instructions
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
[http://www.cgsecurity.org/wiki/Menu_Analyse](http://www.cgsecurity.org/wiki/Menu_Analyse)
repairs including testdisk info & link to testdisk, testdisk is in repository and on most repairCDs
[http://members.iinet.net.au/~herman546/p21.html](http://members.iinet.net.au/~herman546/p21.html)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)

---

### Post by xioSlayer on 2012-08-02
Are you saying I deleted my ubuntu installation?  I selected the partition that had windows on it whenever I reformatted that partition.  I don't think I understand though :[  It took me a while to get everything set up on ubuntu (apache, ssh, iptables, etc), but do you think it might just be easier for me to start over and reinstall ubuntu?

---

### Post by oldfred on 2012-08-02
No it looks like you deleted your original /home partition which was separate when you installed. When you rebooted without it, it will create a new /home folder in / but if you had customized any user settings in /home they would be missing. If you recover the /home partition you may get those settings back.

The applications are still installed and device settings in /etc will still be there.

---

### Post by xioSlayer on 2012-08-02
How did I delete the Home directory by reformatting windows?  So I can not do it again?  I will try to use those links you sent me hopefully it works.

---

### Post by oldfred on 2012-08-03
DId you use Windows to delete partitions. It has been known to not handle extended partitions correctly. Not sure if it is Windows or other Windows partitioning tools. Best to use Windows tools to shrink (or expand) the Windows NTFS partition and do everything else with gparted from either the Ubuntu liveCD or a gparted or parted magic liveCD.

---

### Post by xioSlayer on 2012-08-03
I just used my windows disk and pointed it to the current windows partition to reinstall.  I thought all this would only ruin grub which could be fixed through the graphical interface.  This is not the case?

I may just need to reinstall ubuntu though because I dont understand what i'm looking for with testdisk.  Thanks for the help anyway.

---

