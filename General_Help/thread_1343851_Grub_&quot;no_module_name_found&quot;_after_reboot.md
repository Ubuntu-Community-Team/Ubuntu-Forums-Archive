---
title: "Grub &quot;no module name found&quot; after reboot"
date: 2009-12-02
forum: General Help
---

### Post by LucasG on 2009-12-02
So I have Windows 7 installed in my machine. I went ahead and installed ubuntu server on another partition. After the installation I was able to either boot to Windows 7 or Ubuntu server through GRUB. But after shutting down my pc, and this morning turning it on, it gave:

> Booting from lcoal disk...
GRUB loading.
no module name found
Aborted. Press any key to exit.

And GRUB won't give any options or anything, like if GRUB got corrupted and now I cannot get into any of my OS's.

Any ideas?

---

### Post by some-what-Gnu-2-networks on 2009-12-02
Get _GAG_ Bootloader. You can probably best get it from the SystemRescueCD. Install that as your bootloader instead of GRUB.

---

### Post by namok on 2009-12-02
@LucasG download [Super Grub Disk]("http://prdownload.berlios.de/supergrub/sgd_cdrom_1.21.iso.gz"), burn cd, boot with it and you should be able to start Ubuntu. [Then you should go back to the grub legacy]("http://ubuntuforums.org/showpost.php?p=8071880&postcount=18"), and then apply the method described here: [http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub).

---

### Post by semacore on 2010-04-30
Have the same issue

I get this...

[COLOR=Navy]no module name found
Aborted. Press any key to exit.
Intel(R) Boot Agent GE v1.3.35
Copyright (C) 1997-2009, Intel Corporation

PXE-E61 : Media test failure, check cable
PXE-M0F : Exiting Intel Boot Agent.
Operating System not found[/COLOR]


I did find this as a solution but it seems to be a temporary solution at best:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

Is there a solution other than wiping the drive?

---

### Post by ONEother on 2010-05-01
Same problem -- every time that Windows 7 starts up/shuts down (I can't figure out which) it manages to override the MBR to create this result.  No Windows 7 loader, no GRUB loader.
The only option I've come up with is booting from the Ubuntu live cd and reinstalling grub on the MBR.  This is a rather lengthy and tedious thing to do every time I want to turn the computer on, windows 7 or ubuntu.  So then I have to decide whether to use Ubuntu exclusively (not likely), use Windows 7 exclusively AND leave it on at all times, or reinstall grub every time I shutdown windows 7.
Curiously, after this proccess, the boot file for bcdedit (in windows 7) no longer exists and the only resolution to this situation is to use the windows recovery/installation disc to rebuild it.
There's gotta be something easier!  What is windows doing that could make grub stop working, or override the MBR on startup/shutdown?

---

### Post by verifiedbuy on 2010-05-01
I think you have to format your hard disk ones.

---

### Post by ONEother on 2010-05-01
So in other words, I need to reformat the entire hard drive?
As far as formatting goes, on first install of Ubuntu I did the half&half (or so) and made Windows the smaller partition.  Since then I have reformatted the new (Ubuntu, ext4 & swap) partitions several times over.  The current system is /dev/sda1 is Dell Utility 41MB FAT16, /dev/sda2 is windows recovery 16GB NTFS, /dev/sda3 is windows 7 126GB NTFS, /dev/sda4 extended partition (sda5 and 6), /dev/sda5 (ubuntu) and /dev/sda6 (swap) are under an extended partition, would that be causing a boot problem?
/dev/sda5 is formatted as ext4 with the extent disabled and the inode size at 128 (not sure what it means, but I was trying to get Windows to read the hard drive as per [these instructions]("http://www.soluvas.com/read-browse-explore-open-ext2-ext3-ext4-partition-filesystem-from-windows-7/").
EDIT: Also, is it advisable/required to have a boot partition on Ubuntu?

---

### Post by ONEother on 2010-05-01
Okay, one more question concerning this.  Since the Dell Utility (diagnostic tool) is the first partition and windows 7 is the second, what does the BIOS try to boot if there is no Ubuntu boot partition?  Or is it grub that's having the trouble?  Note again the error message "no module name found" and after you "press any key to exit" it displays the chipset and "no operating system found".

---

### Post by snijkerm on 2010-05-14
Same problem for me. Just installed Ubuntu 10.04 LTS on a Dell laptop preinstalled Win7. Each time Win7 has started up no booting possible anymore. Unless you reinstall grub. Which is not workable obviously. Any suggestion on how to make it work would be extremely welcome.

Someone suggested to configure bootloader inside Windows? I have no idea how to do that??

Working with Ubuntu for more than 4 years nicely next to WinXP. Never had any issues. This thing is a real showstopper. What is Windows doing? First time startup I had a diskcheck inside windows. Subsequent times no check but always this problem of not being able to restart afterwards.

Is it a Win7/Dell (Studio7) issue only?

Thanks,
Marcel

---

### Post by aoszkar on 2010-05-15
Same here. New Dell laptop with Windows 7. I installed Kubuntu 10.04 LTS, and it worked fine for a few days, then I suddenly got the "no module found" error followed by the "Operating System not found" message.

It seems you have to reinstall GRUB with the Live CD (see [http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/](http://www.howtogeek.com/howto/ubuntu/reinstall-ubuntu-grub-bootloader-after-windows-wipes-it-out/)).

But I still haven't found a way to make this permanent 
Any ideas? Is Windows 7 really this intrusive?

---

### Post by oldfred on 2010-05-15
Dell & HP have software that writes into the MBR that corrupts grub2.

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
In Windows 7, I had to remove Windows 7 DataSafe.
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)
[http://ubuntuforums.org/showthread.php?t=1344828](http://ubuntuforums.org/showthread.php?t=1344828)

---

### Post by aoszkar on 2010-05-16
Thanks for the info. The instructions on the sourceforge page did the trick:
> sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda

I uninstalled DataSafe now. But I had installed Microsoft Security Essentials the other day, and it might have been guilty of writing to the MBR.

---

### Post by johnrobert on 2010-05-21
I also think this is a Dell software problem. I've been running 9.10 and then 10.04 next to Windows 7 on my Dell Studio for several months now. But last night I finally went ahead and let the Dell Recovery software set itself. And now I have the the same boot failure that was reported by semacore. And when I ran fdisk -lu (after booting from a live CD), it shows the first 63 MB of my hard drive now being taken up by "Dell Utility."

I just made the fix described by aoszkar, and am going to reboot. Wish me luck.

---

### Post by johnrobert on 2010-05-21
And we're back!

Thanks to oldfred, aoszkar, and everyone else who pointed me right here. I'm going to go find out how to remove the guilty piece of Dell crapware and report back.

---

### Post by johnrobert on 2010-05-22
I logged into Windows and removed both pieces of software for "Dell DataSafe" and that has fixed the problem.:guitar:

---

### Post by sbarn on 2010-05-23
It is not just Windows. I just purchased a Dell Latitude 13n laptop with only Ubuntu installed. After running the dell-recovery-media to create a factory restore disk it similarly trashed my MBR. I booted on a live disk USB stick and repaired it as noted above using grub-install (on the Latitude the root directory is /dev/sda3).

---

### Post by akihito_tan on 2010-05-26
> **johnrobert said:**
> I logged into Windows and removed both pieces of software for "Dell DataSafe" and that has fixed the problem.:guitar:

I too had the same problem. Started with dell studio... Installed ubuntu 10.04 LTS 64bit...
Everything works fine and after creating dell recovery media and booting into win7, it killed grub...
sigh...

Been booting using super grub disc...not a permanent solution

I am just wondering, after logging into windows...removed dell "datasafe"...will there be any impact to the machine?
after removing, we still have to reinstall grub, right?

(sorry noob in ubuntu...)

---

### Post by lillypilly on 2010-05-28
I have also had the same problem with a brand new Dell Studio 1747.  Installed Ubuntu 10.04 and restarted several times. Went back into Win 7 and on the first reboot got the problem. Fortunately I found several threads on the net through Google and was able to get back into Ubuntu and restore Grub. Tried going back into Win7 and each reboot it failed. Removed the Dell Datasafe programs and have had no further problem.

---

### Post by joanluc+ on 2010-06-10
Hi all, I noticed, most of the people having troubles with Grub had it in conjonction with Windows 7 but i can report the same problem with a multiboot between Ubuntu 10.04, RedHat EL 5 and Windows XP.

As long the PC didn't boot Windows, no problem, but after that windows session, grub was erased so i needed to boot with the "Super Grub Disk"'s CD to have grub reinstall under Ubuntu.

At that time, i think the reparation is not definitive as i just made a default re-installation of Grub, but the explanations i found about aren't very helpfull as i did'nt found nor *stage1*, nor *stage1_5*, nor *stage2* grub file ...

I found this in [http://www.supergrubdisk.org/wiki/WindowsErasesGrub#Technical_explanation](http://www.supergrubdisk.org/wiki/WindowsErasesGrub#Technical_explanation)
"
Find all the files in your system with the pattern: *stage1_5*  usually found at /boot/grub and /usr/lib/grub and rename them ( or move  them to a backup directory). 
After that reinstall grub with grub-install or root and setup  commands. Do not reinstall it with apt-remove and apt-get install! 
When grub-install doesn't find the *stage1_5* files it will know  that you want to link stage1 directly to stage2. 
Check this link for details on running grub-install [http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC10](http://orgs.man.ac.uk/documentation/grub/grub_3.html#SEC10) 
e.g.  
**For the first sata drive** 
grub-install /dev/sda 
**For the first IDE drive** 
grub-install /dev/hda
"

---

### Post by oldfred on 2010-06-10
If you did an upgrade from a system running grub legacy 0.97 prior to 9.10 then you probably still have grub legacy. 

New installs of 9.10 and upgrades from that or new installs of 10.04 have grub2. The instructions for reinstalling grub or grub2 are totally different.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by ealias on 2010-06-12
I have this problem but i have found a solution ...

First, the use of supergrub disk cdrom allow to boot windows 7 and ubuntu 10.04. Burn this image [http://developer.berlios.de/project/showfiles.php?group_id=10921]("http://developer.berlios.de/project/showfiles.php?group_id=10921")

After we can use the sotfware easybcd 2.0 (2.0 is mandatory for Win 7) 
to restore the bootloader of Win7 (so win7 start from the disk) ans to add an entry to ubuntu 10.04 in this bootloader .

Follow this procedure : [http://doc.ubuntu-fr.org/tutoriel/comment_amorcer_ubuntu_avec_bootmgr](http://doc.ubuntu-fr.org/tutoriel/comment_amorcer_ubuntu_avec_bootmgr)

---

### Post by postorganic on 2010-06-21
I have the same problem.
I guess it could be because the system is installed in a logical partition.

---

### Post by effinriot on 2010-07-05
Hi my names Austin and im having the same problem you guys are.
A little about my situation is i have a Alien ware M17x r2 laptop. A Friend suggested i try Linux on my computer but i didn't want to give up windows so he said partition it off and give it like 50gigs. I say ok well will try that. I decided to just take my empty external and put the os on there and boot form that. Make a long story short i worked intill i updated it and restarted. I get the following error now:

no module name found
Aborted. Press any key to exit.
Intel(R) Boot Agent GE v1.3.35
Copyright (C) 1997-2009, Intel Corporation

PXE-E61 : Media test failure, check cable
PXE-M0F : Exiting Intel Boot Agent.
Operating System not found

I dont know what to do. Im stuck because i know my hd weren't touched by this os so there intacted but yet it wont let me get to my win7 os. I cant do anything in bois to help me and im not reformatting because i have a 1tb hd and thats just alot of stuff to recover. Can someone please help me out. Also just to let you guys know im am a total noob to this. like im pretty sure that im pretty good with this kinda stuff but just keep in mind thanks.

---

### Post by oldfred on 2010-07-06
Yours looks like a BIOS error even before windows or grub boot. 

This may be the problem:
Some bios refuse to boot a hard drive without a boot flag. Although linux/grub  does not need one.
More precisely: Some Bios require a boot flag on a primary partition.
So it is not important that the first partition has the boot flag, but that one of the first four partitions has a boot flag.

You can use gparted or disk utility from LiveCD or 
set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda

---

### Post by baderfgt on 2010-07-09
I got this problem right after I updated my Dell n5010 BIOS. The BIOS updated fine and I have the new one that was released  on 06.29.2010 yet it didnt boot from the hard drive after the first restart. I used a liveCD and these 2 lines and they fixed it. just be careful with the spaces. it didnt work with me from the first time.

> **aoszkar said:**
> Thanks for the info. The instructions on the sourceforge page did the trick:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```


I uninstalled DataSafe now. But I had installed Microsoft Security Essentials the other day, and it might have been guilty of writing to the MBR.

---

### Post by uduogah on 2010-07-20
> **effinriot said:**
> Hi my names Austin and im having the same problem you guys are.
A little about my situation is i have a Alien ware M17x r2 laptop. A Friend suggested i try Linux on my computer but i didn't want to give up windows so he said partition it off and give it like 50gigs. I say ok well will try that. I decided to just take my empty external and put the os on there and boot form that. Make a long story short i worked intill i updated it and restarted. I get the following error now:

no module name found
Aborted. Press any key to exit.
Intel(R) Boot Agent GE v1.3.35
Copyright (C) 1997-2009, Intel Corporation

PXE-E61 : Media test failure, check cable
PXE-M0F : Exiting Intel Boot Agent.
Operating System not found

I dont know what to do. Im stuck because i know my hd weren't touched by this os so there intacted but yet it wont let me get to my win7 os. I cant do anything in bois to help me and im not reformatting because i have a 1tb hd and thats just alot of stuff to recover. Can someone please help me out. Also just to let you guys know im am a total noob to this. like im pretty sure that im pretty good with this kinda stuff but just keep in mind thanks.

Hi Austin, just use the supergrub disk or ubuntu livecd as the others above and restore your grub bootloader. it's no bios error as some would suppose. those bios messages are just your pc trying to boot from pxe etc.

---

### Post by mbickell on 2010-07-23
Same problem, running Lucid on a Dell Studio with win 7 preloaded.

I tried to remove the Datasafe in Windows, but it gives me an error every time (like its being used - I'm pretty sure I stopped all instances in the task manager), I even tried removing it when in safe mode and I got the same error. 
Is anyone else having problems removing Datasafe? Any advice?

Thanks.

---

### Post by addiraj on 2010-08-08
It is the problem with new laptops of dell.
can anyone tell why this happens ?

---

### Post by techmedia on 2010-08-08
It is the vista bootloader which has been corrupted. To fix it download EasyBCD and install it on your windows 7 and fix the vista bootloader. then add your your other OS ubuntu in the EasyBCD software and reboot the machine and it should work. see link [http://www.sevenforums.com/tutorials/5110-dual-boot-change-os-name-windows-boot-manager.html](http://www.sevenforums.com/tutorials/5110-dual-boot-change-os-name-windows-boot-manager.html)




> **snijkerm said:**
> Same problem for me. Just installed Ubuntu 10.04 LTS on a Dell laptop preinstalled Win7. Each time Win7 has started up no booting possible anymore. Unless you reinstall grub. Which is not workable obviously. Any suggestion on how to make it work would be extremely welcome.

Someone suggested to configure bootloader inside Windows? I have no idea how to do that??

Working with Ubuntu for more than 4 years nicely next to WinXP. Never had any issues. This thing is a real showstopper. What is Windows doing? First time startup I had a diskcheck inside windows. Subsequent times no check but always this problem of not being able to restart afterwards.

Is it a Win7/Dell (Studio7) issue only?

Thanks,
Marcel

---

### Post by Dakra on 2010-08-20
> **aoszkar said:**
> 
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda 			 		


Thank you aoszkar, it worked here! 
I have a new Dell Inspiron1545 on which I immediately installed Ubuntu 10.04 next to Windows 7. Everything worked fine the first day but I just got the no module name found problem at restart today.

I'm outraged by all those crapware, pre-installed without the user authorisation.

---

### Post by cloudsea on 2010-08-23
I guess before you restarted, you were using windows. If so, most likely, some program(s) in windows modified the mbr (master boot record).

In this case, you can fix the problem using a Ubuntu installation CD without reformatting the whole hard drive. When computer is starting up, choose to reboot from CD. ~ 15 minutes later, there will be a screen asking whether you want to try out Ubuntu or install Ubuntu. Select try out Ubuntu. Go to the terminal to fix the problem following this guide:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Zavatustra on 2010-08-26
> **johnrobert said:**
> I logged into Windows and removed both pieces of software for "Dell DataSafe" and that has fixed the problem.:guitar:

It works! Tanks guy!!!

---

### Post by iarenoob on 2010-08-26
Deleting Dell datasafe worked for me.  
Is this problem because of the fact that dell datasafe handles the "recovery" partition, which also happens to be marked boot?

Previous comment mentioned this: [http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
which appears to be a different but strikingly similar problem, did any1 get that solution to work?

---

### Post by wtflinux on 2010-08-27
I have an ASUS G50V and this is extremely annoying. I get the "no module name found" error and there is no way I can enter the bios. My bios is set to boot from hd first and does not even check to see if there is a disc in the drive to boot from. The only thing I can think of is physically resetting the bios. What a pain, I'll not be using ubuntu again.

---

### Post by DJ29Joesph on 2010-08-29
I'll stay with virtual box till a permanent fix comes through for this.

---

### Post by iarenoob on 2010-09-01
@wtflinux, why are u unable to enter ur bios?

---

### Post by HighburyTiger on 2010-09-05
Hi there, I've been lurking on this forum for the last couple of days  and have found it very useful in resolving my Ubuntu/Windows 7 problem - thanks to everyone who has contributed!   As such, I thought I'd post to share my experiences in case they come  in useful for anyone else (_however, please bear in mind that I am very  new to Linux and hence you should take the below with a large pinch of  salt, before you start to duplicate my actions!_)  I also have a related question about the MBR - please see the end of this  post.
 
 **Details of my system and the problem**
 
[LIST]
[*]System: new Dell 1749 laptop with Windows 7 pre-installed.
[*]Procedure being carried out: installation of Ubuntu on the same hard drive to create a dual-boot system.
[*]Problem: following Ubuntu installation and subsequent use of  Windows 7, GRUB2 (the Linux bootloader) failed to start when the  computer was rebooted, giving the "no module  name found" error message as discussed on this forum. This prevented me from starting either operating system.
[/LIST]
  **How I fixed it**
 I initially tried to reinstall GRUB2 using the instructions here:  [COLOR=Blue][https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)[/COLOR]   However, due to my lack of experience with Linux I found this quite  tricky.  As such, I eventually gave up and went for the brute force  approach of reinstalling Ubuntu from the live CD (I didn't lose any data  through doing this, as I had booted into Windows straight after the  original Ubuntu installation and hence GRUB2 was broken immediately,  before I'd used Ubuntu for more than about 30 seconds!)

The reinstallation of Ubuntu allowed me to recover GRUB2 functionality.   I was thus able to boot up Windows 7 and uninstall the Dell  DataSafe programs (I'd already used the local program to create the Dell  restore DVDs for Windows 7, so I figured I wasn't losing too much by  deleting it).  This session in Windows 7 obviously caused GRUB2 to fail  once again when I rebooted, so I reinstalled Ubuntu once more in order to  recover GRUB2.  This solved the problem - I now have a fully functional GRUB2 that doesn't get killed by using Windows 7!
 
**Related question**
If I have any further problems with GRUB2, I'd like to find a quick and  easy way to restore it (reinstalling Ubuntu is clearly not a sustainable option!)  The methods outlined in the link above will  presumably work if I've become more comfortable with Linux commands.   However, I wonder if there is an easier (albeit potentially more risky) way to fix the problem.

My  understanding is that GRUB2 fails in the above scenario because another  program (Dell DataSafe, for example) writes to the MBR (Master Boot  Record - the code that sits at the start of the computer's hard drive  and tells it what to do when the system starts up) and hence overwrites  the code for the first stage (stage1) of GRUB2.  In contrast, I assume  the code for the second stage (stage2) of GRUB2 remains intact in the  /boot partition elsewhere on the hard drive.  If this is correct, then  presumably all that needs to be done to regain GRUB2 functionality is to  restore the stage1 code to the MBR (as opposed to reinstalling the  whole of GRUB2).

Thus, my question is as follows: if I create a backup  of the first 446 bytes of the MBR, can I simply use this to restore  GRUB2 should another Windows 7 program decide to tamper with the MBR?  The following site contains a detailed explanation of how the MBR is  backed up and restored:  [COLOR=Blue][http://members.iinet.net.au/~herman546/p13.html#mbr_dd]("http://members.iinet.net.au/%7Eherman546/p13.html#mbr_dd")[/COLOR]  I'd be really  interested to hear from any experienced Linux users as to whether they'd  recommend this approach, or whether they'd steer well clear.  As far as I can see, the main con may be that it  is easier to really mess up your system by getting the 'dd' command wrong,  whereas reinstalling the whole of GRUB2 (stage1 and stage2) using the 'grub-install' command may be a more foolproof option.  One  pro, however, might be that any GRUB2 customisation (splash image, font  changes, etc.) saved in the /boot partition (stage2) would be retained, rather than overwritten.

Any thoughts on the above would be most appreciated.  I'd like to reiterate that _ I'm very new to Linux, so please wait until a more knowledgeable user replies with their guidance before you make use of this idea!_  Thanks.

---

### Post by mhtcirl on 2010-09-19
> **cloudsea said:**
> I guess before you restarted, you were using windows. If so, most likely, some program(s) in windows modified the mbr (master boot record).

In this case, you can fix the problem using a Ubuntu installation CD without reformatting the whole hard drive. When computer is starting up, choose to reboot from CD. ~ 15 minutes later, there will be a screen asking whether you want to try out Ubuntu or install Ubuntu. Select try out Ubuntu. Go to the terminal to fix the problem following this guide:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)


Thanks for the link...nice and simple fix

---

### Post by FeRe on 2010-10-25
Hello, I've an Alienware Mx15 and my problem is

no module name found
Aborted. Press any key to exit.
Intel(R) Boot Agent GE v1.3.35
Copyright (C) 1997-2009, Intel Corporation.

PXE-E61 : Media test failure, check cable
PXE-M0F : Exiting Intel Boot Agent.
Operating System not found

My solution was: "Install Burg, it is a small aplication wich change boot"

---

### Post by cliff60 on 2010-10-25
ive got a sim prob but im getting grub loading. error: no such partition. grub rescue> ive tried to use my win7 recovery disk but i get the same msg when it reboots.  recovery is only finding the windows partition but cant reboot. how do i get rid of the grub loader and ubuntu partition? ubuntu crashed after getting a virus and i cant get into windows either. all i got from klam was it was a worm right before it crashed. everything was crashing for a few days before it totally went.

---

### Post by efflandt on 2010-10-29
**cliff60** it sounds like you may have a different issue.  If a virus corrupted Windows or your hard drive you may need to properly connect the drive as a secondary drive or in USB enclosure, boot Windows on that computer (but not from that drive), and run chkdsk /f X: (substituting actual drive letter of your drive for X) from a command window.  Then you should virus scan any Windows partitions on that drive from the other computer.

Back to the subject, the problem is that grub2 is larger than the DOS/Windows mbr, so some nasty Windows programs use what they "think" is empty space there to store things.  That corrupts grub2 and it fails.

After running 64-bit Maverick (beta, RC, and release) on a Dell Studio XPS 8100 from USB hard drive, I finally did a regular install to my internal drive.  I intended to put grub on sda4 (a primary partition), but overlooked that in manual partitioning during install, and grub ended up in my mbr.  Everything worked fine until I booted 64-bit Win7.  After that when I tried to boot all I got after BIOS splash screen (with no clue what was generating that error):

[B]no module name found
Aborted, press any key to exit[/B]

When I pressed enter it just said:

[B]No boot device available
wait for enter key to retry
SATA 1 : Installed
SATA 2 : Installed
SATA 3 : None
SATA 4 : None[/B]

(1 is hard drive, 2 is DVD/CD drive).  Pressing enter then just took me back to the first error.  The only way out of that was the power button.

Fortunately I could boot Ubuntu on the internal drive from grub on the usb hard drive.  **sudo grub-install /dev/sda** fixed grub so I was able to boot.  But next time I ran Win7, same problem.

I used grub on usb to boot my internal drive again and tried "sudo grub-install /dev/sda4", that bitched (why?), so I had to **sudo grub-install --force /dev/sda4**.  From Win7 DVD I did **bootrec /FixMbr** to restore the Windows mbr.  Then using gparted on usb Ubuntu, I set /dev/sda4 as the boot partition.  So now everything works fine dual boot despite those nasty Windows programs.

But I have only tried installing grub to a primary partition, not an extended or logical partition, so I do not know if that works.  I know that before grub, lilo used to be able to boot from an extended partition with standard mbr, but not from a logical partition. If you have any primary partition that is not the boot partition of another system, grub can be installed there (although, it will complain).

---

### Post by A Mystical Badger on 2010-11-06
So I have the same problem mentioned above, except when I booted up windows, i only had a black screen and my mouse cursor, leading me to believe my explorer.exe was deleted. I tried ctrl+alt+del, but it didn't do anything so i powered down. Then when I booted up again, I got this error exactly how I type it: 

"no module name found
Aborted. Press any key to exit.
Intel UNDI, PXE-2.1 (build 083)
Copyright (C) 1997-2000 Intel Corporation

This Product is covered by one or more of the following patents:
US5,306,459, US5,434,872, US6,570,884, US6,115,776 and
US6,327,625

Realtek PCIe GBE Family Controller Series v2.29 (06/30/09)
PXE-E61: Media test failure, check cable
PXE-M0F: Exiting PXE ROM.
Operating System not found
_"

I think that cause my windows explorer.exe is gone, that I allocated too much space for the Linux partition, so it overwrote some of my windows files. I don't know this for sure, but that's the only thing I can think of. I do have a Dell studio 15, so i also have the dell datasafe crap, so that may have screwed up my mbr as well. I think I'm gonna try to remove the Linux partition off my hard drive and do a system restore to recover/fix my mbr. Is it possible to delete my Linux partition from booting from the ubuntu LiveCD?

---

### Post by Talruk6 on 2010-12-28
I've been having the problem mentioned in this topic for a while, but I only recently noticed this post on it.  ](*,)

I had a separate topic here:  [http://ubuntuforums.org/showthread.php?p=10121416#post10121416](http://ubuntuforums.org/showthread.php?p=10121416#post10121416)

I was about to use the fix from this thread, when I found I had a new twist on this problem.  When I booted up my computer with the Live CD inside I got the following new message:

```

BusyBox v1.13.3(ubuntu:1:13.3-1ubuntu11) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount:  mounting/dev/loop0 on //filesystem.squashfsfailed:  Input/*tput error

can not mount /dev/loop0(/cdrom/casper/filesystem.squashfs) on //filesystem.s*ashfs



****Note:  where I added the symbol * it looked like some of the text was cut off because it trailed off on the monitor****

```

Between the old message and the new message, the only thing I've done is leave the computer on for 6 hours and then turn it off manually by holding the button down (since I can't get into the OS to turn it off properly).

Some quick googling showed that "BusyBox" is a minimal shell that pops up when there is a problem with the booting process.

Does anyone have any ideas on what's going on here?  I'm wondering if I should just swap out the hard disk drive for a new one, if that would even work.

---

### Post by Jabrouwer on 2011-01-27
The previous solution worked for me


Re-boot from the liveCD
enter the following into the command line:

```
sudo mount /dev/sda5 /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sda
```

restart, boot to Windows
Uninstall Dell DataSafe (maybe take a reboot, which also required me to do the liveCD step again)

On second reboot, everything appeared to work fine.

---

### Post by almayer on 2011-01-30
Thank you Jabrouwer, your solution solved completely my problem!

---

### Post by Houghmandy on 2011-06-30
Thank you Jabrouwer.  This solved it for me also.

---

### Post by George Heine on 2011-07-31
I dual-boot on an HP Compaq nc2400:  WinXP and Ubuntu 10.04. 
Only boot into XP occasionally, no problems up to now.  However, recently needed
to install software (Apple Qucktime) on the XP side; perhaps this is what caused the
"no module name" problem.

At any rate, the fix posted by aoszkar worked for me.
Thanks for your help.

---

### Post by Denny Johnson on 2012-01-28
Thought I'd add my experience to the knowledge base.
Ubuntu 10.04 LTS and Windows XP. infrequently use the XP for design programs.
I got tired of the annoying Dell Data Safe and McAfee pop ups, so uninstalled those programs.
That's when I lost the bootscreen and got the "no module name found" msg.
I employed cloudsea's solution in post #31, worked well.
Thanks cloudsea.

---

### Post by neilybob on 2012-04-04
Another addition to the knowledge base:

I have a Dell Inspiron dual boot system (Ubuntu / Win7). I've ignored the Dell Datasafe utility till yesterday when I inadvertently started the program. I cancelled it after it ran for a minute and thought nothing more of it till I started up this morning and got the "no module name found" message and was unable to access the boot menu.

Fortunately I had a bootable Ubuntu thumb drive. Booted Ubuntu via the thumb drive, made a network connection, opened a browser and Googled up this Ubuntu documentation on boot repair:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I followed Option 2 (install Boot-Repair in Ubuntu) and it worked, restored the Grub boot menu when I rebooted.

I booted into Win7 and did some further Googling on the subject and found this thread which implicates Dell Datasafe... so, I uninstalled Datasafe, rebooted and... it corrupted the MBR again!

I redid the USB thumb drive Ubuntu boot up and repeated the boot repair. I've since booted up both Win7 and Ubuntu with no problems, apparently the problem is solved.

FWIW

---

