---
title: "using ubuntu 9.04, can't change vista partition with gparted"
date: 2010-04-13
forum: General Help
---

### Post by Dustin2128 on 2010-04-13
I'm trying to install jaunty at the moment, running off of live CD, and for some odd reason, the excellent sliding partitioner in hardy has been removed and I have to prepare my partitions beforehand. Unfortunatley the reason I am installing ubuntu on this particular computer is because (surprise) windows failed:lolflag:. Basically this means, although I'd be happy to install 'buntu to my whole HDD, I, or more specifically, some relatives, have important data on the windows partition making this unacceptable. I tried changing the vista partition size via GParted, but all the options are greyed out and I can't even give myself a not so generous 100GB of space. (180GB~ free space on HDD). Any help would be greatly appreciated, but if I loose this data (and through extension, the gov't looses their precious income taxes)... just no. No.

---

### Post by blubaustin on 2010-04-13
Try resizing the hard drive in vista. Vista has a Computer management program that allows the resize of ntfs, and works perfectly.

---

### Post by 2hot6ft2 on 2010-04-13
A screenshot of gparted would help but I suspect that you have something mounted that you need to unmount or a swap partition that you need to turn swapoff by right clicking on it and selecting it.

Also in the installer when you get to the partitioner select Manual and click Forward to start the manual partitioner then you can have more control.

---

### Post by Dustin2128 on 2010-04-13
By vista failed, I mean I cannot boot into vista or I would've fixed the drive partition. As for the gparted screenshot...
Going to go to bed now, so just keep up with my thread for feedback/screenshots/whatever

---

### Post by sandyd on 2010-04-13
> **Dustin2128 said:**
> By vista failed, I mean I cannot boot into vista or I would've fixed the drive partition. As for the gparted screenshot...
Going to go to bed now, so just keep up with my thread for feedback/screenshots/whatever
good evening from the resident nightcrawler.

sir/madam, your vista partition is corrupted, and as a result it cannot be resized. if you look at it, it indicates that there is no unused space nor used space, and there is a excpamation mark beside the partition. That indicates corruption and/or problems with the partition
If you need to recover data from the drive, you can use a program called testdisk.

---

### Post by Dustin2128 on 2010-04-13
Ah, I suspected disk corruption, I just didn't know it could mess with partitioning (Software, not hardware junkie). As for files, would anyone here know where turbotax/quicken files are stored in their respective default directories? Thank you in advance.

---

### Post by oldfred on 2010-04-13
Have you tried running the windows repairs on the windows partition. Gparted & Ubuntu will not normally mount a partition that has a flag set to require chkdsk. Only if the windows repairs do not work you can force a mount but it may damage it more. Testdisk then is the best solution.

Always run chkdsk and run again until there are no errors, that may be all that is required
How to use the Bootrec.exe tool in the Windows Recovery Environment to troubleshoot and repair startup issues in Windows
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)
Repair often does not work, some say run 3 times others recommend the command line bootrec.exe

You will need to boot with your Vista/Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr   #updates MBR master boot record  do not run if you still want grub
chkdsk /r 
BootRec.exe /FixBoot  #updates PBR partition boot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP(they create the boot sectors differently) but can run check disk.

---

