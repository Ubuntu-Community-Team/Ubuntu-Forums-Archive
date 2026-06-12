---
title: "Deleted Ubuntu Partition --&gt; Can't get past Grub Loader/Rescue"
date: 2011-10-01
forum: General Help
---

### Post by acepilot on 2011-10-01
Hi Guys, I've made a simple mistake that seems pretty hard to solve.  

1.  I had a HDD partitioned as Windows XP and Ubuntu
2.  I deleted the Ubuntu partition while in Windows, reformatted the Drive 
3.  Now when I boot I get the grub rescue console.
4.  I need to get it to boot to windows. 

I've tried fixboot and fixmbr from a Windows XP installation file on a USB.

I have no CD drive.

When I try to boot into Knoppix using another USB Drive the screen goes crazy. I was having this problem with Ubuntu, thats why I got rid of it, I guess its Linux in General, its one of those netbooks with atom installed. 

I am completely lost for ideas, any help would be much appreciated. 

Thanks

---

### Post by MG&amp;TL on 2011-10-01
Well....if you have an install disk, I would say it is not as difficult as you think. Boot from whatever you can (try various CDs/ live USBs), copy your data onto something external.

Reinstall windows.

Am I missing something?

What sort of crazy?

---

### Post by acepilot on 2011-10-01
I don't want to reinstall windows.  

Pretty much the only options I have is to run a command from grub rescue or the windows xp recovery console.

Note: I'm getting the Unkown File system error and then the grub rescue console

---

### Post by acepilot on 2011-10-01
OK, here's a question, I know how to change the set prefix and set root options in the grub rescue console, but how do I then get grub to boot into the changed prefix.

---

### Post by MG&amp;TL on 2011-10-01
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

Does this help?

---

### Post by acepilot on 2011-10-01
getting close...almost there...should have it solved soon...

---

### Post by MG&amp;TL on 2011-10-01
Good luck. I think people should make it a bit clearer what the protocol for removing ubuntu is.

---

### Post by acepilot on 2011-10-01
So I've almost got there,  I found a utility called "Super Grub Disk", which is basically a bootable version of Grub2, which I've installed onto a USB thumb drive using UNetbootin.  Now, I'm supposed to be taken to the Grub2 console to follow these instructions [www.supergrubdisk.org/wiki/UninstallGRUB](www.supergrubdisk.org/wiki/UninstallGRUB) , which should uninstall my grub and restore the proper windows boot sequence.  

I am now facing a new problem which is that UNetbootin won't load Super Grub Disk...I'm thinking maybe the problem lies with the size of my USB thumb drive which is 16GB, I've read that this can cause problems.  

I also have a 1GB drive but the problem is that Windows XP is on that and I don't want to take the risk of deleting XP. 

I'll try a few more things and see how it goes.

---

### Post by MG&amp;TL on 2011-10-01
Take a look at the link about installing grub from ubuntu live cd.

---

### Post by drs305 on 2011-10-01
If I understand your situation correctly attempting to restore the Grub bootloader isn't going to work. While you may get to the Grub rescue prompt, if you deleted the Ubuntu partition Grub isn't going to be able to load the commands to allow booting Ubuntu or Windows. You can't run Ubuntu and you also can't load the modules which would allow any boot of Windows.

If you can get to the Ubuntu desktop, or if the rescue methods you are using allow you to install linux apps,  you can install 'lilo' and reset the MBR to point to your Windows partition. If the Windows boot structure and files are intact you should be able to boot.

Otherwise you will have to find a way to boot to Windows and repair the bootloader using Windows apps.

---

### Post by acepilot on 2011-10-01
> **MG&TL said:**
> Take a look at the link about installing grub from ubuntu live cd.

Thats a problem, like I said this pc seems to hate Linux, any time I try to load up any sort of Linux based console the screen simply goes crazy.  Sometimes I get what looks like pixelated static and other times vertical orange bars. I just hope the Super Grub Disk doesn't do the same since it is Linux based. Anyway, still need to get it working...

---

### Post by MG&amp;TL on 2011-10-01
Hey, drs!

Would not installing the bootloader get it to read the partitions again?

---

### Post by drs305 on 2011-10-01
> **MG&TL said:**
> Hey, drs!

Would not installing the bootloader get it to read the partitions again?

My understanding is that the Ubuntu partitions have been deleted but Grub 2 information is still written on the MBR. From the Grub rescue prompt, there are only a few basic functions available. The 'ls' command is there, but at best it can see existing partitions. I don't believe it would see any partitions that have been deleted. It's not capable of seeing deleted partitions, nor capable of restoring them.

The bootloader only points to the files on a partition. Since the partition has been deleted, I don't think any bootloader has that capability. The partition structure could be restored using Testdisk, but that would entail being able to boot to some usable form of linux as well. If that is possible, installing 'lilo' would probably be easier.

There is a version of SuperGrub that will boot Windows. It's been many years since I had to use it, but I imagine it's still available in one form or another.

---

### Post by acepilot on 2011-10-01
Thanks for your input drs.  You're right with your assumptions.  Ubuntu is gone, the partition is gone, its been reformatted back to NTFS, but grub is still on the MBR (and I think its Grub1 not 2 if I'm not mistaken).  

The good thing is that the solution to my problem is here [http://www.supergrubdisk.org/wiki/UninstallGRUB](http://www.supergrubdisk.org/wiki/UninstallGRUB)

But to be able to run the instructions above I have to get Grub onto a bootable USB.  This is where I'm at right now. 

I'm a little confused and having problems with Super Grub Disk, I'm assuming that it is not the entire Grub program but just a installer that allows for Grub2 to be booted from a USB/CD? I have tried downloading Super Grub Disk and then using UNetbootin to load it onto a USB stick, hasn't worked.  I don't think I'm doing it right because the UNetbootin console opens up on boot but with nothing on it, no Grub. So thats why I'm assuming I haven't actually installed Grub2 on it, UNetbootin is just a program that makes it bootable?

I am now exploring the method put forward here [http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/](http://www.pendrivelinux.com/install-grub2-on-usb-from-ubuntu-linux/).  Should have Ubuntu downloaded in the next hour(s).  

Any idea how to get the entire Grub Loader onto a USB without having to download Ubuntu.

---

### Post by acepilot on 2011-10-02
I thanks for the Help, Problem Solved.

I don't quite know what did it but I followed the following steps

1.  Downloaded and ran Rescatux Linux Rescue Disk.  It has a Boot Manager Wizard which I used and chose to "Fix Window MBR".  (This completely removed Grub).  However Windows was still unable to boot, just got a blank screen with "MBR 1:" and a flashing cursor that did nothing. 

2.  Installed Windows 7 onto a separate partition and ran EasyBCD.  This at least fixed the boot problems and I was now able to chose between Windows XP and Win7.  However, WinXP still wouldn't boot getting: NTDetect Failure. 

3.  Loaded up Windows 7 and replaced NTDetect file in XP with copy from XP install CD.  Problem Fixed. 

I had to first remove the HDD and place it in a computer with a cdrom drive and hardware that would run linux.  Original acer aspire netbook in which the problem occurred had neither a cdrom drive and had hardware issues (screen trouble) with linux based OS/Live Disks.

---

