---
title: "Windows 7 won't boot"
date: 2011-12-18
forum: General Help
---

### Post by Sigma1 on 2011-12-18
Hello,
I installed Ubuntu 11.04 on my daughter's machine; with Windows 7 next to it. Both booted to begin with, but now Windows appears to have stopped booting. When I choose Windows from the boot screen, it returns to the grub boot menu, after a few brief seconds of the Windows logo.
I've tried getting Windows to repair the problem as well as using the grubrepair tool, and reinstalling 11.04 from scratch, but the symptoms persist.
I'm not really fussed about booting into Windows, but it is annoying to have 250Gb sitting there doing nothing, and annoying generally to have things that don't work as they should do!
I'm posting the output from the bootinfo script as well as a gparted screenshot. There may be something very obvious that I'm missing here! Any help much appreciated.

---

### Post by 2F4U on 2011-12-18
To what partition does grub point to? It may point to the system partition (/dev/sda1) instead of the Windows partition.

---

### Post by Sigma1 on 2011-12-18
Thanks for your answer. I'm not sure how I found out which partition grub points to... Here's the output from the beginning of bootinfo. Are the first lines here the indicator?

              Boot Info Script 0.60    from 17 May 2011


============================= Boot Info Summary: ===============================

 => Grub2 (v1.99) is installed in the MBR of /dev/sda and looks at sector 1 of 
    the same hard drive for core.img. core.img is at this location and looks 
    for (,msdos5)/boot/grub on this drive.

sda1: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /bootmgr /Boot/BCD

sda2: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows 7
    Boot files:        /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda3: __________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        

sda4: __________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  Unknown
    Boot sector info:  

sda5: __________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 11.04
    Boot files:        /boot/grub/grub.cfg /etc/fstab /boot/grub/core.img

sda6: __________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

============================ Drive/Partition Info: =============================

---

### Post by grvsaxena419 on 2011-12-18
Hello Sigma1,
> **Sigma1 said:**
> Hello,
 When I choose Windows from the boot screen, it returns to the grub boot menu, after a few brief seconds of the Windows logo.
You are getting the windows logo that means grub is right in passing control to windows bootloader, you should try reinstalling windows bootloader manually, try booting windows7 dvd and go to recovery console and use 
```
 	**Bootrec.exe /FixMbr**
**Bootrec.exe /FixBoot** 
  **Bootrec.exe /RebuildBcd**

```
If after this you get windows boot loader and are able to boot into windows try restoring grub using grub-install.

---

### Post by dieseleldo on 2011-12-18
Nvm, follow grvsaxena419's advice. It will delete the grub bootloader however, so be prepared.

---

### Post by Sigma1 on 2011-12-18
Hello and thanks for your answers; I have tried:

```
 	**Bootrec.exe /FixMbr**
**Bootrec.exe /FixBoot** 
```

from the recovery menu (the machine didn't come with a DVD!), but didn't try: 
```
  **Bootrec.exe /RebuildBcd** 
```

If I follow you correctly, then if this works, I'm going to have trouble booting from ubuntu, so I'll probably have to boot from a live CD, chroot into / and reinstall grub from there. Is that right?
Thanks in advance!

---

### Post by dieseleldo on 2011-12-18
Yes, you will need the livecd to re-install grub again. Also, before you reboot after fixing grub, open your grub.cfg and make sure that the Windows 7 entry is chainloaded.

---

### Post by Mark Phelps on 2011-12-18
Don't mess with grub.cfg -- period.

After you reinstall GRUB, it's very likely that you will then boot directly into Ubuntu.

Then, open a terminal and enter "sudo update-grub".  That will regenerate the grub.cfg file.  

When you then reboot, you should get a GRUB menu allowing you to select Ubuntu or Win7.

---

### Post by Sigma1 on 2011-12-19
Thanks again. One last question before I start hacking into the machine: where should I put grub? Where it is now, or on another part of the disk?

---

### Post by grvsaxena419 on 2011-12-20
Hello Sigma1
> **Sigma1 said:**
> Thanks again. One last question before I start hacking into the machine: where should I put grub? Where it is now, or on another part of the disk?
You should put grub in /dev/sda which is the default so most probably its there presently. But if you have again the same problems with booting into windows you might think of putting grub in some partition eg. /dev/sdaX where X represents partition number like 1,2 , etc.
You could see the instructions for installing grub from here [http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275) goto section 13. This will suit you most probably.

---

### Post by Sigma1 on 2011-12-20
Thanks for the answers. I can't even get windows recovery to boot now, and, since the machine didn't come with a windows 7 boot dvd, I'm going to borrow one, and see what I can do from there. (Things like the ultimate boot cd etc. do not apparently include Bootrec.exe.)
If there's any progress, I will post it here.

---

### Post by lindsay7 on 2011-12-20
Take a look at this info,

download and burn this iso disk.

[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

here is some info on it,

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by Sigma1 on 2011-12-20
Thanks for the link. I tried boot-repair (I had tried it once before), but, although it told me it had repaired something, the symptoms persist. I think I'll have to get W7 to sort out the MBR first, if I want to keep WIndows on the machine!

---

### Post by lindsay7 on 2011-12-21
When you used and ran the Boot-repair disk, did you try to run the restore mbr option first and then run the reinstall grub option.

---

### Post by Sigma1 on 2011-12-21
Thanks for following this up. Yes, I did do things that way round.
For what it's worth, I got the following urls, the first from the mbr fix, and the second after reinstalling grub:
[http://paste.ubuntu.com/776503/](http://paste.ubuntu.com/776503/)
[http://paste.ubuntu.com/776506/](http://paste.ubuntu.com/776506/)
Thanks again.

---

### Post by lindsay7 on 2011-12-21
Did you do any partitioning of the windows partition. That can screw up the windows installation.

---

### Post by Sigma1 on 2011-12-22
Yes I did repartition the disk before installation. Windows 7 had set up sda1 and sda2 for itself (most of the 500Gb) and put the partition for the backup tool on sda3 at the end of the disk. That meant I had to resize sda2, create a fourth, extended partition, sda4 between sda2 and 3 and put ubuntu there. The gparted screenshot in my first post (below) might make things clearer.
Perhaps if I removed sda3 altogether, and freed up the space, that might help the Windows bootloader...

---

### Post by Mark Phelps on 2011-12-22
> That meant I had to resize sda2

HOW did you do this?  Did you use the Win7 Disk Management utility to do it? IF so, did you reboot into Win7 afterward and was it still then working OK?

Since you apparently can lay hands on a Win7 DVD, there are several different approaches you could use to get Win7 working again.

Recomment you check out the following section in the Win7 forums (sevenforums.com):

[=Installation%20and%20Setup"]http://www.sevenforums.com/tutorials/?filter[3]=Installation%20and%20Setup]("http://www.sevenforums.com/tutorials/?filter[3)

---

### Post by Sigma1 on 2011-12-22
Thanks again for the answers.

> **Mark Phelps said:**
> HOW did you do this?  Did you use the Win7 Disk Management utility to do it? IF so, did you reboot into Win7 afterward and was it still then working OK? 

No, I'm pretty sure I must have used gparted to resize things, probably on installation.

> **Mark Phelps said:**
>  Since you apparently can lay hands on a Win7 DVD, there are several different approaches you could use to get Win7 working again. 

Unfortunately I don't have a Win7 DVD, no. I'm asking around though. If the worse comes to the worse, I might end up having to fork out $9.75 and but the recovery disk at [http://systemdiscs.com/](http://systemdiscs.com/)

> **Mark Phelps said:**
>  Recomment you check out the following section in the Win7 forums (sevenforums.com):

[=Installation%20and%20Setup"]http://www.sevenforums.com/tutorials/?filter[3]=Installation%20and%20Setup]("http://www.sevenforums.com/tutorials/?filter[3)

I'll do that, thanks.

---

### Post by lindsay7 on 2011-12-26
If you had windows on a partition and used gparted to re-size the windows partiton. I think you windows installation is going to be unusable. I have had this happen to me in the past and nothing I could do made it recoverable. I am not saying it is impossible, just that I could never find a way to do it  I have also had this problem when I have tried to clone a windows partition to a larger or smaller partition on another drive. Windows just does not like to be messed with in terms of any change to its partition size. I tried using the Disc-Repair program and had the original windows installation disk. I tried fixmbr, fixboot, etc from the recover options and also ran the startup repair over and over and had no luck.

---

### Post by Sigma1 on 2011-12-28
Thanks Lindsay7, that was rather what I was afraid of! Still, I'm going to try and manage something with a Windows7 DVD, if I can, even if it involves reinstalling Windows on the machine, and will post the result, when it happens.
Otherwise, Ubuntu will just have the 500Gb to itself :D.

---

### Post by oldfred on 2011-12-28
Have you also run chkdsk as well as fixboot? They depend on each other (so you may have to run each more than once) and the chkdsk is the first thing Windows runs when it resizes itself.

---

### Post by Sigma1 on 2011-12-29
Thanks oldfred and lindsay7. I gave it a go, and ran the bootrec.exe commands three times; it told me things were fixed, but, on booting, I went from the Windows boot manager screen, to the very beginning of the Windows7 animation, then back to the boot manager, and so on, in a loop.
It seems like I can only now try to restore the whole thing to factory state, using the Windows7 recovery disk, then reinstall ubuntu from there, doing my partitions from within Windows, this time round.
I'll see whether my daughter wants it doing, and whether the little hair I have left will take the accumulated stress! ;)

---

### Post by oldfred on 2011-12-29
Did you alternate chkdsk & fixboot? And if chkdsk has an error you have to run it until there are no errors.

---

### Post by Sigma1 on 2011-12-30
Thanks, oldfred, for the answer. No, I haven't run chkdsk yet. I'll do that. I imagine I should be running something like: chkdsk c: /f /r is that right?
A couple more questions, though, before I begin. Is there a command along the lines of df, which would tell me whether I should run chkdsk on C or D? Are C and D used for different partitions or just for different physical disks, and, if C, D etc. are different partitions then should I run chkdsk on all the ntfs partitions I've got?
Sorry to be asking so many questions, but it's a long time since I worked with Windows, and I prefer to get the command right, rather than to have to explain the symptoms of another mess up!
Thanks!

---

### Post by Sigma1 on 2011-12-30
I've just run chkdsk from the W7 CD, but chkdsk c:, d: and e: all return no errors at all.
I can't even return the thing to factory state, since the recovery disk I've got is not meant for the same computer.
Too bad, I think Ubuntu is going to get it all!

---

### Post by Sigma1 on 2012-01-07
Well, I can't really claim victory, but here's how things stand. I backed up /home, ordered a recovery DVD from Lenovo (a little under 20 euros) and used it to restore the hard disk to its original state, i.e. three partitions sda1 (C:\) called SYSTEM_DRV (a quirk of Lenovos), sda2 (D:\) the hard disk with W7 and sda3 (E:\) with the recovery images. I then repartitioned using the W7 partitioning tool. I couldn't shift E:\, so just reduced D:\. I then installed Ubuntu on the unallocated disk space left in between D:\ and E:\. Things appear to be working more or less as expected since then.
When a brand-new computer has three partitions already, that does not leave many installation possibilities, which is annoying.
I think, as one contributor has pointed out, that the problem might have lain with my use of gparted (0.5.3, I think) to resize partitions, since, when partitioning in NTFS, older versions of gparted like this required the user to uncheck the default "round to cylinders" paramater, cf. [http://gparted-forum.surf4.info/viewtopic.php?id=14779](http://gparted-forum.surf4.info/viewtopic.php?id=14779).
A learning experience, I suppose, which I will marked "solved" for want of a better word. Thanks to all for your pointers!

---

