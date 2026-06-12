---
title: "Boot Manager Question"
date: 2012-05-04
forum: General Help
---

### Post by airspoon on 2012-05-04
Hello, I just recently completed building a new system and of course installed Ubuntu right away. However, I haven't used Windows in a very long time (Vista pretty much turned me completely off) and because Windows 8 Consumer Preview is free, I decided to try it out. Long story -short, my impressions of windows lightened a little and am now wanting to install Windows 7, along side Ubuntu. 

However, because I'm using relatively small SSDs (120gb), I've decided to install Windows 7 on its own SSD. Right now, I have Windows 8 on one SSD and Ubuntu 12.04 on another SSD and the boot manager that comes with Ubuntu doesn't load Windows at all. I'm having to go into the UEFI or BIOS to select the windows disk in order to boot into Windows.

With that said, I'm now wanting to replace Windows 8 with Windows 7 and I remember hearing many years ago that on a dual boot system, you should always install Windows first because it does something that makes other OS's installed not bootable. Is this still true? If so, would installing a new boot manager after I install Windows 7 be a viable solution?

Regardless, is there any open-source or otherwise free boot managers that I can install after I install Windows 7?

Any and all help would be greatly appreciated!

---

### Post by zombifier25 on 2012-05-04
Ubuntu already comes with a boot manager: GRUB.
The reason that you must install Windows BEFORE Ubuntu is Windows will overwrite Ubuntu's GRUB with its own, BOOTMGR, which will NOT detect any OS but Windows.
Since you're using two SSDs, it kinda depends on what SSD you have your bootloader. I'm not really knowledgable about this, but if you install BOOTMGR on one drive and GRUB on another, set your computer to boot off the GRUB one and go into Ubuntu, type this in the terminal:
```
sudo update-grub
```
Ubuntu should be able to detect the Windows installation.

---

### Post by pqwoerituytrueiwoq on 2012-05-04
with multiple drives you can install windows 2ed without issues you simply unplug the power to the drive with ubuntu on it, once that is done install windows on the other drive then reconnect the power to ubuntu's drive and run update-grub as root
you may need to go into your bios and change which hard drive has priority for booting afterwards

---

### Post by oldfred on 2012-05-04
Are you booting in UEFI mode or BIOS. UEFI may be a bit different.

Note that Windows 8 defaults to essentially hibernation and with dual booting hibernation is not a good idea.
WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
But then files may be corrupted similar to Windows 7 Hibernation:
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)

---

### Post by airspoon on 2012-05-05
Thanks for all of the replies.

"Are you booting in UEFI mode or BIOS. UEFI may be a bit different."

I have UEFI, though not sure if that means that I'm booting in UEFI mode. When I boot my computer, it automatically brings me to grub. If I want to boot into Windows, I have to go into UEFI to select the proper disk to boot. During UEFI start-up screen, I can press "F11" which gives me an option to select the disk without going all the way into UEFI, however the UEFI start-up screen lasts only a second or two -at most, so I have to be really quick, which is kind of annoying.

So, even though I have UEFI, are the other two posts valid, where I can simply update grub to get Windows to boot from the grub screen? Also with UEFI, am I still able to disconnect the SSD with Ubuntu when I install Windows 7 in order for Windows not to mess with grub?

Thanks!

---

### Post by oldfred on 2012-05-05
I do not know the details of UEFI. I assume you still set a default drive to boot from and that drive has to have an efi partition to have the efi boot loader.

You should be able to disconnect a drive and use UEFI to start the installer from either Windows or Ubuntu. That will then install to that drive in UEFI mode by updating efi partition.

Some discussion here:
dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)
Has chainload window efi grub entry:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)
Dual boot UEFI & windows UEFI post 76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)

---

