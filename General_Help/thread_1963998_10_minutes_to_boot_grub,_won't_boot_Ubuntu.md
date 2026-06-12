---
title: "10 minutes to boot grub, won't boot Ubuntu"
date: 2012-04-23
forum: General Help
---

### Post by LunaticStrain on 2012-04-23
I recently installed Ubuntu 10.04.4 alongside Windows 7. After restarting without the CD all I see is a blank screen with a flashing cursor for around 5 to 10 minutes, then it brings up the boot options such as linux, linux recovery, windows 7 etc. I figured the GRUB installation was messed up, so I tried boot-repair, but I hear there is a problem with that in 10.04.4 and as such I upgraded to 11.whatever. Except now, it still takes 5 to 10 minutes to get to the boot selection screen, and if I choose my ubuntu it goes to a blank screen with a blinking cursor, which I left overnight, and it never changed.

 If I go into recovery I see a ton of information, it looks like it's looading drivers etc. At a certain point it just hangs and doesn't move anymore. I am seeing something about 188.397527] usb 2-1.3: usbfs: interface 0 claimed by usblp while usb sets config #1

It is important to point out what, while it took WAAAY too long to get to the GRUB loader before, I could still get into Ubuntu 10.04.4 or 10.10(I believe that number is correct). I cannot even boot into 11.anything. If it helps I have a USB mouse and keyboard, and when I installed Ubuntu I had a portable USB hard drive plugged in. I was worried it has installed GRUB onto that, but seeing as how it still works, just takes forever, I don't think that is the case.

Any help would be greatly appreciated, thank you.

Billy

---

### Post by Mark Phelps on 2012-04-23
I encountered similar problems with 10.x versions to the point that I quit using them.  But what I find would work some of the time was booting into Recovery Mode and selecting the option to Repair broken packages.

After that, I was able to reboot OK -- for a while.

---

### Post by LunaticStrain on 2012-04-23
Ok, new update. I made an 11.10 live CD and it won't boot into it. It stops at a USB detection, but I have no USB devices plugged in at the moment. If I use the old 10.04.4 live CD it boots in no problem. Any idea why this would be happening? Does my computer just not support Ubuntu 11 and up?

Thanks again for any help.

---

### Post by LunaticStrain on 2012-04-23
Another update, and this time it's even weirder. IF I boot up with my Windows 7 CD in the drive, it brings up the GRUB bootloader very quickly, and if I choose my Windows 7, or 'Previous Linux Versions' then it boots into those fine. If I choose the current linux distro, it never loads, even after doing recovery and fixing packages and grub. Also, if I reboot without the windows DVD in the drive, it takes 10 to 15 minutes to load the GRUB bootloader. I honestly have no idea what to do at this point. I was going to just load up my windows 7 DVD and format the hard drive and just reinstall windows, but I only have an upgrade edition. It'd have to buy the older version, or a new copy of windows 7.

Obviously I can boot into windows now, which is nice, but having to have the windows CD in the drive is very weird, not to mention the fact that it's on a DVDRW and I am starting to think that the bootloader was installed onto it, possibly erasing my windows 7 data.

**EDIT**
Ok, when I boot from the live CD of 11.10 it always hangs at the same location, usb 2-1.7: new fuyll speed USB device number 3 using ehci_hcd

Some googling tells me that Ubuntu just might not support my hardware, specifically USB 3.0 in this case. As such what I am going to try to do is boot into my windows 7 cd, go to the command prompt and attempt to rebuild the windows boot record. If I can do that, then I will just format the partition that had Ubuntu on it. Wish me luck.

Thanks in advance for any help.

---

### Post by YannBuntu on 2012-04-24
Hello

> **LunaticStrain said:**
> IF I boot up with my Windows 7 CD in the drive, it brings up the GRUB bootloader very quickly, and if I choose my Windows 7, or 'Previous Linux Versions' then it boots into those fine. If I choose the current linux distro, it never loads, even after doing recovery and fixing packages and grub. Also, if I reboot without the windows DVD in the drive, it takes 10 to 15 minutes to load the GRUB bootloader. I honestly have no idea what to do at this point.


Please could you check your boot order in your BIOS settings?
Maybe currently you have , eg: CD > USB > Network > HardDisk
You should setup like this: CD > USB > HardDisk > Network

Also, please could you indicate your [BootInfo URL]("http://ubuntuforums.org/showpost.php?p=11136267&postcount=1") ?

---

### Post by LunaticStrain on 2012-04-24
I'm not home right now, but I'll post that info as soon as I get there.

---

### Post by Mark Phelps on 2012-04-24
OK, first of all, do NOT reinstall Win7.  That has absolutely nothing to do with GRUB working or not.

Second, you've mixed the terms of Win7 CD and Win7 DVD -- so I can't tell what disk is doing what when you use it.

Win7 does not come on a CD; if you have a CD and your PC came with Win7 preloaded, that is most probably a Restore CD, and if it does boot, it's most likely booting into WinePE, not into Win7.

Unless you wrote GRUB onto the DVDRW, along with Win7, I can see no reason why a GRUB menu would show up when you boot from either Win7 disk -- unless you wrote GRUB to your hard drive and it's actually booting from there.

So, just to be clear, can you boot all the way into a Win7 desktop without any disk inserted?

---

### Post by LunaticStrain on 2012-04-25
Ok, I've had some time to mess with the settings and figure out some things. Sorry for the confusion from before. I have only 1 Windows 7 disc and it is a DVDR, legit copy, student edition upgrade from Windows Vista. As a DVDR I know it didn't install the boot record there.

If I go into BIOS settings and I have it try and boot from the disc drive first, it takes 10-15 minutes to get to GRUB, unless I have ANY disc in the drive, then it is a matter of seconds. If I change this to HDD first, it goes right to GRUB. 

With or without the DVD in the drive I can boot into windows 7 perfectly fine. I can also boot into two Previous Versions of linux,
Ubuntu, with Linux 2.6.35-32-generic-pae  Opens but no internet connection.

Ubuntu, with Linux 2.6.32-40-generic-pae  Opens but no internet connection.

But it still won't boot into Ubuntu 11.10. If I try it goes to an almost brown colored screen and never changes, even after hours. If I turn off Legacy USB support it goes instead to a black screen with blinking cursor.

If I use an Ubuntu 11.10 Live CD is gets to

[3.909625] usb 2-1.7: new full speed USB device number 3 using ehci_hcd

I have enabled the EHCI hand off option in BIOS, and also tried again with it on, and it doesn't seem to help either way.

I now have 2 things I need to figure out:

1) How to get Ubuntu 11.10 running, and why it isn't now. To that end I have an Asus 1155 P8P67 Motherboard and Intel Core i5 CPU.

2) If I can't get Ubuntu 11.10 working, I'd still like to manage to get the internet working in the older versions of Ubuntu, so if anyone know where I can find a network driver for my motherboard for Ubuntu, let me know. Keep in mind I'd have to download it on one computer, then transfer it via USB to my main computer.

Thank you for any help you can provide. I would have included the boot-repair URL thing, but it won't connect to the internet. As I said above, I believe that it is a driver issue, but I'm not sure.

---

### Post by oldfred on 2012-04-25
Asus has lots of versions, so these may not apply, but were other Asus users issues:

Asus m4a87td  core unlocker feature on usb3 was causing the problem
Asus - Security> I / O interface Security> "New interface card" or so. SET IT TO LOCKED!!! 
In the Asus BIOS I selected Advanced Mode>Advanced>SATA Configuration.

What video do you have? That often is the screen issue.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Natty or later Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

---

### Post by LunaticStrain on 2012-04-25
My video card is Nvidia GeForce 560 ti. I'll try those boot options and see what I can find out.

---

### Post by LunaticStrain on 2012-04-26
I just wanted to give an update. My problem seems to be mostly solved. The problem with booting into Ubuntu 11.10 was that I needed to add nomodeset to the boot options. Now it boots in just fine. It still takes 10-15 minutes to get to grub if I have the bios settings set to DVD then HDD. If I have any CD or DVD in the drive it goes to grub instantly, and if I choose to boot from HDD first it goes to grub instantly, so that's what I'm doing for now. I can always change it if I need to, so I'm not too worried.

Thank you so much for the help, you guys are great. This is why I love the Ubuntu community.

Thanks,

Billy

---

### Post by gordintoronto on 2012-04-26
This indicates a hardware problem with your optical drive, since the problem occurs before any software is loaded.

---

