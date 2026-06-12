---
title: "Multi-booting my system with Ubuntu 11.04"
date: 2011-09-30
forum: General Help
---

### Post by soumyabratapaul on 2011-09-30
Hello, I have a system which has already Windows 7 Ultimate 32-bit and Windows XP SP 2 32-bit. I now want to install Ubuntu 11.04, in my computer.

Can someone, actually tell me the precise steps, that it would require to install the OS.

Also, if I install, Ubuntu 11.04 along side my Windows 7 and Windows XP, then my Windows Boot Manager, will cease to exist, and the GRUB2 Bootloader will come automatically and, will the GRUB2 boot loader automatically update itself, to include the other 2 Windows OS, or do I have to do it manually?

Thanks for all your help in advance!

---

### Post by pravin10t on 2011-09-30
............

---

### Post by Blasphemist on 2011-09-30
I'd use windows disk management to shrink one of its partitions and create enough free space for ubuntu but DO NOT do partitioning in windows. Also, how many existing partitions do you have? Ubuntu will need to create an extended partition and within that create its logical partitions. There is a bios/mbr limit of 4 primary partitions so it's possible that you already have 4 used. When you boot to the ubuntu live cd/usb, choose try ubuntu and then run GParted to look at the partitions. If you see 4 that already exist or have any other questions, post the screen shot and ask.

---

### Post by soumyabratapaul on 2011-10-03
Sorry, for the late reply. Here is the information that you had requested for.

---

### Post by soumyabratapaul on 2011-10-03
Here is the screen shots with Ubuntu 10.04, running, GParted.

---

### Post by Blasphemist on 2011-10-03
> Hello, I have a system which has already Windows 7 Ultimate 32-bit and Windows XP SP 2 32-bit. I now want to install Ubuntu 11.04, in my computer.

Can someone, actually tell me the precise steps, that it would require to install the OS.

You have an unusual partition configuration on both of your drives. You have one primary partition on each drive and extended partitions on each drive that each have multiple logical partitions within them. Part of each partition is used but between them there is quite a bit of unused storage. Each extended partition has the LBA flag set and win 7 boots from one of those logical partitions which is quite rare and some would say it doesn't work. Apparently it does when the extended partition has the LBA flag set.

The first thing you need to do is to empty one or more of your logical drives. sda7, sda8, sdb7 and sdb8 all look like good candidates. sda7 and sda8 are each plenty large enough. You could using GParted make sda8 smaller to make room for a swap partition. Then you'd format sda8 as EXT4 and during installation set its mount point as /. In the newly unallocated space from shrinking sda8, you'd create sda9 and make it a swap format partition. This new sda9 should be just a bit larger than the amount of memory that you have. I'd make these changes prior to starting ubuntu installation. Then when you are installing ubuntu you'll go through choices like time zone, language and keyboard before you come to the disk allocation screen. At that screen choose the manual option (it may be labeled "something else"). Ubuntu will know automatically to use the swap partition that you already created so you don't need to do anything with it. You'll select the sda8 partition (if you choose that partition to resize when using gparted) and choose edit. Ensure that partition is set to EXT4 format and set the mount point as / (root). You can label it as Ubuntu or something appropriate if you want but a label isn't required.

About all that is left is to tell the installation to write the boot loader (grub2) to the device you are installing to (sda if you use the sda8 partition as I've described.
> Also, if I install, Ubuntu 11.04 along side my Windows 7 and Windows XP, then my Windows Boot Manager, will cease to exist, and the GRUB2 Bootloader will come automatically and, will the GRUB2 boot loader automatically update itself, to include the other 2 Windows OS, or do I have to do it manually?

Yes, the installation of grub2 will scan the system for the windows installations and include them as boot choices.

---

### Post by oldfred on 2011-10-03
Because you have two drives, I would strongly suggest installing Ubuntu to the second drive. Then your windows drive will not be changed at all and if you have to you can in BIOS reset to directly boot windows in the Windows drive - sda or Ubuntu with grub2 in sdb. But when you install Ubuntu it defaults the install of the grub2 boot loader into the sda drive. You have to use manual install or Something else in Natty to get a choice on where to install the boot loader which should be the sdb drive.

Lots of detail (may be a lot for a new user, but worthwhile is you really want to know details)
Installing Ubuntu in Hard Disk Two (or more) internal or external 
Maverick screens shown, other versions have slight difference in screens but process is the same.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Windows only boots from the active partition or boot flag in Linux. Grub2's os-prober will find your windows installs and set up boot fro them, but your second install of Windows has no boot files as they have been moved to the first install.

Discusses Vista but 7 is the same except 7 has a 100MB boot partition in addition.
To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

Since one install is XP, you can probably move boot files back to XP partition, possibly edit boot.ini for correct partition and grub will then boot XP directly, but we can worry about those details after you get Ubuntu installed and dual booting.

---

### Post by soumyabratapaul on 2011-10-04
Can I install Ubuntu 10.04 in my first hard drive/disk(hda) and the GRUB2 in my second hard drive/disk(hdb)?

---

### Post by Blasphemist on 2011-10-04
Yes you can but you'll have to be sure to choose the "something else" manual disk allocation option when you are at the disk allocation step of the install. I believe its during that step when you are able to direct where to install grub2. You'll choose sdb for the second drive.

---

### Post by soumyabratapaul on 2011-10-04
> **Blasphemist said:**
> Yes you can but you'll have to be sure to choose the "something else" manual disk allocation option when you are at the disk allocation step of the install. I believe its during that step when you are able to direct where to install grub2. You'll choose sdb for the second drive.

You are talking about this? And it is ok, to install Ubuntu in my first hard drive/disk(hda) and the GRUB2 in my second hard drive/disk(sdb)?

What will happen if I instead install GRUB2 in my first hard drive? I know I will have to do some manual editing and then update my GRUB. Is this correct, and can you give me some information about that.

---

### Post by oldfred on 2011-10-04
You can install grub2's boot loader to any or all drives, but it is not recommended to install to partitions normally.

I prefer to have each operating system on a separate drive and an operating system on every drive. And have the MBR of that drive be able to at least boot the operating system on the drive. That way if any drive fails, then I can boot the other drive.

A few have issues with Windows 7 and grub2 on the same drive. It relates mostly to DRM software or some windows virus software that thinks grub2 is a virus. Many users seem ok with grub2 on the same drive as they only have one drive. 

Grub2's os-prober finds other operating systems and sets them up to be booted from grub2.

Some thoughts on operating systems on every drive. I do not use Knoppix but use Ubuntu, but he does discusses some issues.
Creating a Dedicated Knoppix Partition for large drives
[http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm](http://www.troubleshooters.com/linux/knoppix/knoppix_partition.htm)
Except I have multiple Ubuntu installs and rotate newest Ubuntu install from drive to drive.

---

### Post by Blasphemist on 2011-10-05
I'm one of the people that Fred refers to that only have one drive and have both win 7 and multiple linux distros on it. I don't have any windows related issue with that. 

Your screen shot of where to choose what drive to write grub to is correct. The advantage of doing what you ask, install grub to sdb, is workable even with ubuntu on sda. It also has a benefit of not touching the windows boot loader in place now on sda. That said, I believe you'd have to either choose your boot drive each time you want to load ubuntu or work fairly hard to get the windows boot loader to pass boot to sdb and ubuntu. And if you choose the second of those two options you end up changing the windows boot loader using bcd or easybcd and that just adds another chance of issues.

I sometimes install distros that use grub instead of grub2 and for one reason or another end up reinstalling or reconfiguring grub2. The one thing that I never have an issue with is booting windows from grub2. But my win 7 installation is standard and yours isn't. It looks like your win 7 isn't in a primary partition and you have both xp and win 7. For now, you may be best off to do as you prefer and not mess with the sda boot loader and install grub2 to sdb. You may decide to change that later when you have more experience. I didn't go right from win 7 only to win 7 and 7 distros, I went standard dual boot for a time, while gaining experience.

---

### Post by soumyabratapaul on 2011-10-07
What if I had only one drive and I wanted to install all the 3 OS, Windows 7, Windows XP and Ubuntu 10.04 there? What are the precise steps that I had to follow?

---

### Post by YannBuntu on 2011-10-08
Welcome among us.

> **soumyabratapaul said:**
> What if I had only one drive and I wanted to install all the 3 OS, Windows 7, Windows XP and Ubuntu 10.04 there? What are the precise steps that I had to follow?

Nothing special, just follow the standard procedure: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

---

### Post by soumyabratapaul on 2011-10-09
> **YannBuntu said:**
> Welcome among us.



Nothing special, just follow the standard procedure: [https://help.ubuntu.com/community/GraphicalInstall](https://help.ubuntu.com/community/GraphicalInstall)

Is this exactly the steps, I need to take when I am installing Ubuntu 10.04 LTS over, 2 previous Windows installations, or are there any other precautions that I need to take, before doing so. Please be specific.

---

### Post by YannBuntu on 2011-10-09
I would just add: don't forget to backup your data on an external device (DVD, USB disk..) before all.

If you have 2 disks, I agree with the previous comments: it is safer to install Ubuntu on the disk that does not contain Windows. :)

---

### Post by soumyabratapaul on 2011-10-12
> **YannBuntu said:**
> I would just add: don't forget to backup your data on an external device (DVD, USB disk..) before all.

If you have 2 disks, I agree with the previous comments: it is safer to install Ubuntu on the disk that does not contain Windows. :)

If I want to do it on my first disk manually, what are the steps that I must follow?

---

### Post by oldfred on 2011-10-12
Backup, create recovery disks, and create a Windows repair disk as any time you are editing partitions on a drive things can go south.


Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Some sites with lots of detail and screenshots:

Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

---

### Post by soumyabratapaul on 2011-10-15
I have already installed Windows XP, and WIndows 7 and the Windows BootLoader is in the dev/sda1. Now I am doing the Ubuntu 10.04 LTS manually, and I am installing the GRUB2 Bootloader in dev/sda? Is this ok, and will this cause any problem, or should I install it in the partition that I am installing Ubuntu, aka the root drive(/), and then edit the partition table using BCDEdit? Which one will be safer and if I want to again go back to my Windows(just asking, I am never going to remove Ubuntu from my system), then what steps should I take, so that my both Windows remains unhampered?

I want to do the first one. Any precautions to take and any manuals that tell me specifically to do this?

---

### Post by oldfred on 2011-10-15
If you are running any proprietary Windows software that uses DRM or a few of the real aggressive virus checkers that think grub2's boot loader in the MBR is a virus then EasyBCD may be better, otherwise it is better to install grub's boot loader to the MBR. 

If using primarily Windows you can use EasyBCD, a few here say it works. But you make grub2 less reliable. Grub2 does not recommend installing to a partition as it has to use hard coded address' to find the rest of grub to boot. Any updates to grub may move the files and break grub, so you then have to reinstall grub.

In all cases be sure to have a Windows repairCd and a current version of the liveCD for every system you install. Then you can repair anything.

---

### Post by soumyabratapaul on 2011-10-16
> **oldfred said:**
> If you are running any proprietary Windows software that uses DRM or a few of the real aggressive virus checkers that think grub2's boot loader in the MBR is a virus then EasyBCD may be better, otherwise it is better to install grub's boot loader to the MBR. 

If using primarily Windows you can use EasyBCD, a few here say it works. But you make grub2 less reliable. Grub2 does not recommend installing to a partition as it has to use hard coded address' to find the rest of grub to boot. Any updates to grub may move the files and break grub, so you then have to reinstall grub.

In all cases be sure to have a Windows repairCd and a current version of the liveCD for every system you install. Then you can repair anything.


I also want to install the GRUB2 in dev/hda, and my Windows bootloader will be in dev/hda, which will in turn boot Windows XP and Windows 7 for me. I also think that this is a good choice compared to others. But what is the exact procedure I must take to actually unistall Ubuntu 10.04 LTS(though I will never do it, I am just asking), if I follow, the first method that I have mentioned to install the GRUB2 in dev/hda?

---

### Post by soumyabratapaul on 2011-10-16
Someone, please comment!

I have 2 HDD (dev/sda and dev/sdb). Forget the sdb, because that is for my back up. I want to get a triple boot system going with Windows XP, Windows 7 and Ubuntu 10.04 LTS. In my dev/sda(that is where I intend to install the 3 OS). dev/sda has 5 partitions, 1 primary(dev/sda1 : Windows XP is installed), and the other 4 extended, logical(lba flag is set). I have Windows 7 in dev/sda5. I intended to install Ubuntu 10.04 LTS in dev/sda7(I will first unallocate it, then make 2 partition within it 1 for / and the other swap, using GParted). Will I have any problem doing it that way. And will the partion where I intend to install Ubuntu (/) will be primary or logical or extended. And if I install the GRUB2 in dev/sda, then when I remove Ubuntu what are the procedure to get my Windows Bootloader back on track.

PS: I have already installed Windows XP and Windows 7.

---

### Post by YannBuntu on 2011-10-16
Hello
- to uninstall your Ubuntu: [https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)
- sda7 is a logical partition. If you split it into several partitions, they will also be logical partitions. I don't see any problem in the procedure you described.

---

### Post by soumyabratapaul on 2011-10-16
Thanks, I am now creating 3 partions, /, /usr and the swap partion. Hang on there, as I am installing Ubuntu right now. And the GRUB2 will be in the dev/sda? This will not cause any problem in the future, if I want to remove Ubuntu or upgrade to a newer version?

What if I want to uninstall Ubuntu manually? Will the OS-uninstaller software bring back my Windows bootloader when I uninstall Ubuntu and GRUB2?

---

### Post by YannBuntu on 2011-10-16
Hello
i don't recommand you to use a separate /usr partition. (for normal user, / and swap is enough, a separate /home can be useful).

>And the GRUB2 will be in the dev/sda? 
i guess yes sda is selected by default, but you can check at the bottom of the partitionning window of the installer


>This will not cause any problem in the future, if I want to remove Ubuntu or upgrade to a newer version?
No.

>What if I want to uninstall Ubuntu manually?
Here is what OS-Uninstaller does :
- restore a generic MBR and make it boot Windows.
- format Ubuntu
If you don't use OS-Uninstaller, you will have to do it manually.

---

### Post by soumyabratapaul on 2011-10-16
I want to know what steps I must take to uninstall Ubuntu it manually?

P.S.: I successfully triplebooted my system with Windows XP, Windows 7 and Ubuntu 10.04 LTS. Yipee!

---

### Post by oldfred on 2011-10-16
Windows uses a simple boot loader that just looks for the active partition (boot flag) and jumps to that to continue booting. You can reinstall the windows boot loader from a windows repairCD which you should create anyway.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

You can install a generic boot loader (Lilo) that works just like the Windows boot loader from an Ubuntu liveCD.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

But I also like to have several repair CDs to fix my system in case something does not boot. YannBuntu's disk is good, I also like Supergrub, gparted liveCD, System Rescue and even a few others (Puppy, Slax) that are just small Linux systems to boot as sometimes the defaults are different and one boots when the other does not. Except now I put most all on one bootable flash drive.

---

### Post by soumyabratapaul on 2011-10-18
> **oldfred said:**
> Windows uses a simple boot loader that just looks for the active partition (boot flag) and jumps to that to continue booting. You can reinstall the windows boot loader from a windows repairCD which you should create anyway.

Make your own Windows recoveryCD/repair:
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

You will need to boot with your Vista/Windows 7 installation disk or repair disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands:
BootRec.exe /fixMBR   #updates MBR master boot record  do not run if you still want grub

You can install a generic boot loader (Lilo) that works just like the Windows boot loader from an Ubuntu liveCD.

Restore basic windows boot loader - universe enabled
Simply open Synaptic and Settings > Repositories and tick the box against the Universe repo in the Ubuntu Software tab. Close that window and click on reload before installing lilo with Synaptic or command line.
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
May show error messages about the rest of lilo missing, ignore, we just want MBR with bootloader.

But I also like to have several repair CDs to fix my system in case something does not boot. YannBuntu's disk is good, I also like Supergrub, gparted liveCD, System Rescue and even a few others (Puppy, Slax) that are just small Linux systems to boot as sometimes the defaults are different and one boots when the other does not. Except now I put most all on one bootable flash drive.

Thanks for all your help! Appreciate it guys! Guess this separates us from proprietary software geeks!

---

