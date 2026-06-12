---
title: "Ubuntu has basically rendered my laptop useless, since I need Windows"
date: 2011-09-29
forum: General Help
---

### Post by kaLuless on 2011-09-29
I have a Compaq 64-bit laptop. I installed Ubuntu alongside Windows, and then decided that, due to the mess in the Windows side due to the previous user, I needed to restore the computer to factory state and start over.

Disaster.

Ubuntu has screwed up the boot sector with GRUB, which the HP restore disc does NOT overwrite, but it does remove the Ubuntu partitions (no option to simply restore Windows). So reinstalling Windows restart brings up the GRUB RESCUE message. Installing Ubuntu makes the machine bootable, but Windows then can't complete the setup process because it can't make sense of the boot partition.

Is there any way from WITHIN Ubuntu to get rid of GRUB?

---

### Post by TeoBigusGeekus on 2011-09-29
Boot up with a windows cd/dvd and choose the repair option.
When you get to a shell, give
```
fixmbr
```
and you're done.
(The above applies to a winxp cd)

---

### Post by oldfred on 2011-09-29
You can use Ubuntu liveCD or many other linux repair CDs that may already have lilo installed.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

If Vista or Windows 7
How to Boot to the System Recovery Options in Windows 7
[http://www.sevenforums.com/tutorials/668-system-recovery-options.html](http://www.sevenforums.com/tutorials/668-system-recovery-options.html)
[http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html](http://www.sevenforums.com/tutorials/20864-mbr-restore-windows-7-master-boot-record.html)
[http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht](http://windows7ultimate.windowsreinstall.com/repairwin7startup/indexthumbs.ht)

Above links summarized, see links if more detail desired
You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

---

### Post by kaLuless on 2011-09-30
> **oldfred said:**
> 
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

Thanks - this appears to have done the trick. I posted this last night in haste before dinner; woke up remembering that bootrec was a step beyond the procedure at the Windows 7 links above, which I had already followed, and which told me it had worked, but in fact it hadn't.

FWIW, I'm a newbie and much of what you said about Ubuntu approaches is a litle daunting, since I'm still trying to get Ubuntu functional and don't know much about it. I also had to figure out that # meant you were putting a comment after the command. Small thing, I know, but had it been on another line there would be no confusion.  Don't mean this as criticism, but hopefully constructive feedback. If the basic nature of my question doesn't give enough hint, the name should ;)

---

### Post by oldfred on 2011-09-30
Glad it works and you figured out the # comment.

I sometimes explain # is comment, but am not consistent. Will try to post explanation everytime.

---

### Post by grahammechanical on 2011-09-30
So, the truth is that the HP restore disk rendered your laptop useless when it removed the Ubuntu partitions and so caused Grub to have nothing to boot. The HP restore disk assumes that there is no need to fix the MBR.

I do not agree that Grub screwed up the MBR. Things were working fine and would still be working fine if as you say

> due to the mess in the Windows side due to the previous user

If you had restored Windows before installing Ubuntu your laptop would not have been rendered useless. I have seen plenty of posts on this forum that say Windows needs to be installed first. 

Credit and blame where it is due.

Regards.

---

### Post by kaLuless on 2011-09-30
> **grahammechanical said:**
> 

Credit and blame where it is due.

Regards.

Fair enough. Actually, 'twas I who messed it up, since I messed with Ubuntu partitions IN Windows, not realizing that GRUB2 directs outside the MBR.

Even with the MBR fixed by Windows, I still couldn't use the restore CDs because the process could not continue beyond them. Details unimportant; it simply didn't work.

Here's what finally worked for me:

1) reinstalling Ubuntu as the only OS (i.e., taking over the whole disk), then
2) restoring from HP restore CDs, then
3) installing Ubuntu (as you say, installing Windows first)

---

### Post by jwbrase on 2011-09-30
Frankly, though it's less convenient for a laptop than a desktop, I prefer, when dual booting, to have Linux and Windows on two totally separate drives. That way you can avoid alot of problems with the two stepping on each other's MBR's (though you still half to be careful. I have, when not paying attention during an Ubuntu install, instructed the installer to write the GRUB MBR to the wrong disk).

---

### Post by viperdvman on 2011-09-30
If you're wanting to install Ubuntu alongside Windows Vista or Windows 7, while keeping the Windows bootloader in the MBR, it's best when installing Ubuntu to install the GRUB bootloader **in the partition that contains Ubuntu**. Then you just manipulate the Windows bootloader to point to both Windows and Ubuntu.

In Windows XP, you actually have to *dd* the first 512 bytes of the Ubuntu partition (must be done in the Terminal, and preferably from a LiveCD/LiveUSB) and name it as "bootubuntu.img" or something to that effect, and put that file in your Windows C:/ drive or onto a separate USB to transfer to the Windows C:/. Then, you just add that to your boot.ini file in Windows. I know there are specific instructions with dual-booting with the Windows XP bootloader in these forums, especially the part on using the *dd* command.

For Windows Vista/7, however, they use a totally different bootloader and must be done differently... and arguably less complex than with WinXP. You would need a program called EasyBCD to manipulate the Windows Vista/7 bootloader, and it makes the process quite easy. I found using EasyBCD on my Win7 netbook to be much easier than setting up dual-boot on my Windows XP as it took much fewer steps to do.

Bottom line, if you're gonna dual-boot with Windows, always install the Windows OS first. Then if you want to use the Windows bootloader to boot your OS's, install Ubuntu and click the option to install GRUB on the same partition as Ubuntu (i.e. **not in the MBR**). I have both my computers set up that way, and it works very well for me. I wish you luck with your dual-boot :)

---

