---
title: "Removing A Full Install of Ubuntu 9.10"
date: 2010-01-21
forum: General Help
---

### Post by andycastille on 2010-01-21
I just installed Ubuntu 9.10 Full Install, and I want to remove it. Ubuntu took control of Windows 7, so if I remove it, it will remove both. How do I fix this problem? I want my laptop to be the way it was 3 days ago.

---

### Post by hwttdz on 2010-01-21
If you installed in wubi you would need to remove through windows.  If you installed on its own partition you can just wipe the partition.  

What do you mean "took control"? If ubuntu is on it's own partition ubuntu can't do anything while windows is running.  If it's in wubi, likewise ubuntu can't do anything unless it's running (unless I misunderstand what this wubi is which I don't think I do, or I underestimate just how silly windows is, which is hard not to do).

---

### Post by andycastille on 2010-01-21
When I press the power button, it shows the VAIO logo then it shows Ubuntu's menu. Ubuntu's menu is:
 
Ubuntu
Ubuntu Recovery
Ubuntu OLD*
Ubuntu OLD Recovery*
Windows Vista (Loader)**
Windows 7 (Loader)
 
*I mean, it says 14 instead of 16.
**I don't even have Vista installed! When I chose this, it opened Windows 7 recovery.
 
***These labels are not in exact words.***
 
Another Thing:
When I had this configeration on my old laptop, I removed Ubuntu by clearing the partition, and when I re-started, Windows was gone and I got an error message:
 
"No operating system was found."
 
This is not a installation inside Windows.
I used the Ubuntu boot menu and chose Install Ubuntu.
 
Any missing information?
 
I am running 64-bit Windows and 64-bit Ubuntu on a 64-bit laptop.

---

### Post by oldos2er on 2010-01-21
Can you please post the output of **sudo fdisk -l** ?

---

### Post by hwttdz on 2010-01-21
> **andycastille said:**
> When I press the power button, it shows the VAIO logo then it shows Ubuntu's menu. Ubuntu's menu is:
 
Ubuntu
Ubuntu Recovery
Ubuntu OLD*
Ubuntu OLD Recovery*
Windows Vista**
Windows 7
 
*I mean, it says 14 instead of 16.
**I don't even have Vista installed! When I chose this, it opened Windows 7 recovery.
 
***These labels are not in exact words.***
 
Another Thing:
When I had this configeration on my old laptop, I removed Ubuntu by clearing the partition, and when I re-started, Windows was gone and I got an error message:
 
"No operating system was found."
 
This is not a installation inside Windows.
I used the Ubuntu boot menu and chose Install Ubuntu.
 
Any missing information?
 
I am running 64-bit Windows and 64-bit Ubuntu on a 64-bit laptop.

First that menu is not the ubuntu menu, that menu is the grub menu, grub is the default boot loader used by ubuntu, but ubuntu is not running when you see that menu (grub which is a sort of mini operating system is).  

Well grub-update searches for operating systems and apparently windows 7 recovery is similar enough windows vista that it fooled grub2.  But the names you can change in your grub configuration, you can also change the default operating system choice, i.e. if you wanted to change the default to windows.

If you clear your ubuntu partition, ubuntu is gone, and if the bootloader (grub or windows boot loader) is on that partition so is the bootloader.  This can be bad.  It's possible that 1) the windows partition is not marked as bootable or 2) you have no bootloader.  So you're going to need to check that you have those things.  I believe you can install the windows bootloader from a windows disk, but you'd need to ask a windows person.  And to mark the partition as boot you can either (use the windows disk possibly?) or use a gparted live cd.  

So by "ubuntu took over" you mean it installed a bootloader which can load multiple operating systems instead of the windows one which seems much less robust?

---

### Post by andycastille on 2010-01-21
I have no idea of understanding for what you said. Can you give it in plain English please?

---

### Post by andycastille on 2010-01-21
> **oldos2er said:**
> Can you please post the output of **sudo fdisk -l** ?
 
I'm using Windows, not Ubuntu. I have Ubuntu installed, but I don't want to switch right now. I'll post the answer I get later.

---

### Post by andycastille on 2010-01-21
I'm booting into Ubuntu, so if I need to do anything in Ubuntu, tell me now.
 
I will give you the output now too.

---

### Post by andycastille on 2010-01-21
> **oldos2er said:**
> Can you please post the output of **sudo fdisk -l** ?

```
****@****-laptop:~$ sudo fdisk -I
[sudo] password for ****: 
fdisk: invalid option -- 'I'

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
****@****-laptop:~$ 
```

Does that help? I'm in Ubuntu now.

---

### Post by hwttdz on 2010-01-21
> **andycastille said:**
> Does that help? I'm in Ubuntu now.

not really, try "fdisk -l" instead of "fdisk -I", or you can just copy and past the original command.

---

### Post by GnubbyaBush on 2010-01-21
K brah, lamens terms time!! 

First off you kinda screwed up, thats ok though. Have you tried both your vista option, and the windows 7 option? If they are both resulting in a windows recovery try to let it recover its boot loader, if for some reason its helpless, then you will need to boot your windows 7 disk again, and hit recovery. What you want to do is a "start up" recovery, where it tries to fix the boot problem. Only thing is it might not work, or if it does, it might overwrite the grub boot loader, meaning you would lose the ablity to boot into ubuntu, but the space would still be taken up by it. Now if you have alot on your current windows and are desperate to save it (and i mean this..because fixing a boot sequence is either a sinch, or a complete S.O.B), then try those things. Otherwise i recomend wiping both partitions (you lose everything), using the windows install disk and then doing the following. 

This is what you should have done in order to dual boot, without losing the windows boot loader. First windows needs to be installed, but when you install it go into the advanced option after clicking custum install (not upgrade), this allows you to specify the size of the partition. default is for windows to use the whole drive..you don't want that cause u want to dual boot. so usually i divide the max number by 2 then put that in and make the partition. now you will have half unpartitioned space and half NTSC partition. Then you go ahead and install windows 7 on that NTSC partition. Once fully completed, and you have actually booted into the windows 7 enviroment then shutdown. Now boot the Ubuntu disk. When the disk eventually boots the partition editor, you will see several options. Even though the default says boot ubuntu side by side with your other OS..this options sucks. Because we actually pre-planned this you have a bunch of unpartitioned space waiting for ubuntu. So you want to choose "use the continuous free space". Continue through the install till you get to the screen where its a summary of what you are about to install. You will see and advanced button, click that and make sure that the check next to "install boot loader" is enabled for hd0. Ok now let it install ubuntu. once your comp restarts. you will have similar options that you have now, exept if you choose windows 7 (sometimes says vista boot loader) it should fully boot no problems..no recovery issues.

---

### Post by andycastille on 2010-01-21
Ok, but Windows 7 goes to Windows 7. I'm in that right now. You mean I need to dig out my Windows 7 install disk?

---

### Post by andycastille on 2010-01-21
Windows 7 is fine. Someone said earlier that Grub thought Windows 7 Recovery was Windows Vista. All Windows is fine, I just want to restore 3 days earlier. System Restore is only in Windows, so it wouldn't restore the boot. I want to remove Ubuntu and go back to only Windows!!! How would I do that? That is all I want to know right now.

---

### Post by andycastille on 2010-01-21
> **GnubbyaBush said:**
> K brah, lamens terms time!! 
 
First off you kinda screwed up, thats ok though. Have you tried both your vista option, and the windows 7 option? If they are both resulting in a windows recovery try to let it recover its boot loader, if for some reason its helpless, then you will need to boot your windows 7 disk again, and hit recovery. What you want to do is a "start up" recovery, where it tries to fix the boot problem. Only thing is it might not work, or if it does, it might overwrite the grub boot loader, meaning you would lose the ablity to boot into ubuntu, but the space would still be taken up by it. Now if you have alot on your current windows and are desperate to save it (and i mean this..because fixing a boot sequence is either a sinch, or a complete S.O.B), then try those things. Otherwise i recomend wiping both partitions (you lose everything), using the windows install disk and then doing the following. 
 
This is what you should have done in order to dual boot, without losing the windows boot loader. First windows needs to be installed, but when you install it go into the advanced option after clicking custum install (not upgrade), this allows you to specify the size of the partition. default is for windows to use the whole drive..you don't want that cause u want to dual boot. so usually i divide the max number by 2 then put that in and make the partition. now you will have half unpartitioned space and half NTSC partition. Then you go ahead and install windows 7 on that NTSC partition. Once fully completed, and you have actually booted into the windows 7 enviroment then shutdown. Now boot the Ubuntu disk. When the disk eventually boots the partition editor, you will see several options. Even though the default says boot ubuntu side by side with your other OS..this options sucks. Because we actually pre-planned this you have a bunch of unpartitioned space waiting for ubuntu. So you want to choose "use the continuous free space". Continue through the install till you get to the screen where its a summary of what you are about to install. You will see and advanced button, click that and make sure that the check next to "install boot loader" is enabled for hd0. Ok now let it install ubuntu. once your comp restarts. you will have similar options that you have now, exept if you choose windows 7 (sometimes says vista boot loader) it should fully boot no problems..no recovery issues.
 
I choose option #1. But Windows 7 works. I'm using it to post this.

---

### Post by michy99 on 2010-01-21
Use your Windows install disk to go into a Windows Recovery mode. Use the command fixmbr. This will over-write the grub boot sector with the regular Windows boot sector. Then you can reformat the ubuntu partitions to use for whatever you want.

---

### Post by andycastille on 2010-01-21
I'll try that in a minute. I have some emails to do now. I'll post the results in about half an hour, so stay watching. :o

---

### Post by michy99 on 2010-01-21
Forget what I just said above. It works a little different with Windows 7. This site shows you how to fix the mbr:

[http://www.ehow.com/how_4836283_repair-mbr-windows.html](http://www.ehow.com/how_4836283_repair-mbr-windows.html)

---

### Post by andycastille on 2010-01-21
Wait...
Will this delete *any *Windows files *at all*?

---

### Post by michy99 on 2010-01-21
It will just replace the grub boot sector with the Windows boot sector that was originally there. Then it will boot straight into Windows like it used to. Then you can do whatever you want to with the Ubuntu partitions.

---

### Post by andycastille on 2010-01-21
Good, I'm going to get my Windows disk now.. Have to reboot.

---

### Post by andycastille on 2010-01-21
Will an Upgrade version work? That's all I have..

---

### Post by andycastille on 2010-01-21
There isn't a 'Repair' option. When I insert the DVD, it loads a dialogue with 'Install Now' as an olny button.

---

### Post by michy99 on 2010-01-21
I found a site with better instructions:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

---

### Post by andycastille on 2010-01-21
Looks confusing... But I can try. Waiting for setup to start.

---

### Post by andycastille on 2010-01-21
Setup Starting... DONE
Preparing Repair... DONE
Loading... DONE
CMDSTART... DONE
CODE... DONE
Fixing... XXXX

AHG! There is no 'boot' in the list for step 4!!! :(

Any other ways?

---

### Post by andycastille on 2010-01-21
THANK YOU! Now stay tuned for more problems in an hour... Really, please do.

---

### Post by andycastille on 2010-01-21
Thanks for the EHOW link, but there isn't a BOOT in step 4? The SEVENFORUMS is on my TO-DO list. 

And the Terminal command answers:

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf9e628ad

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         995     7990272   27  Unknown
/dev/sda2   *         995        1008      102400    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3            1008       17164   129770586    7  HPFS/NTFS
/dev/sda4           17165       30401   106326202+   5  Extended
/dev/sda5           17165       29857   101956491   83  Linux
/dev/sda6           29858       30401     4369648+  82  Linux swap / Solaris

```I have *no idea* what that means, so I hope you will.

---

### Post by thermal_dl on 2010-01-21
I didn't get any disk with my Sony Vaio laptop.
It came with Windows 7 installed.  I bought brand new from BestBuy.
Was I supposed to get some disks?

---

### Post by iseeuu on 2010-01-21
> **michy99 said:**
> I found a site with better instructions:

[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)

Thanks michy99 for linking to my Tutorial!  :D

In the above Tutorial, I had to use the command: bootsect /nt60 SYS /mbr
to replace the Grub boot loader with the Windows one. The Tutorial has been updated. One can use either the Install DVD or you can have 7 create a "System Repair" CD:

[http://www.sevenforums.com/performance-maintenance/51100-repair-cd-system-repair-disk.html](http://www.sevenforums.com/performance-maintenance/51100-repair-cd-system-repair-disk.html)

I hate to see someone remove their Ubuntu from their computer, I think Ubuntu is the best Linux out there. I am moving from 9.04 to 9.10 at the moment.

Cheers!

---

### Post by Jackzor on 2010-01-21
Download this.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

OR use windows 7 to create a windows repair disc.(I would do this)(It works better)

[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

---

### Post by iseeuu on 2010-01-22
> **Jackzor said:**
> Download this.

[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

OR use windows 7 to create a windows repair disc.(I would do this)(It works better)

[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Thanks, Jackzor, for posting those links. If one fubars his 7 computer, has no DVD disk, and didn't have the foresight to create a "System Repair" CD, it is nice to be able to get a copy online (if one is careful to avoid the infected stuff!!).

Cheers!
Robert

---

### Post by andycastille on 2010-01-22
I just want to thank everyone for the help. It worked!
 
--andycastille :D

---

