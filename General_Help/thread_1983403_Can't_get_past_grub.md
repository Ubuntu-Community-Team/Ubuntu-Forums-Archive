---
title: "Can't get past grub"
date: 2012-05-20
forum: General Help
---

### Post by MC Fox on 2012-05-20
I get "Grub" in a dos type screen.  I plug in everything I can think of including "Ubuntu" and nothing happens.  I reboot... same thing.  I have to re-install Ubuntu and it may last for a day or two.  I do not get a recovery mode option.  I am new to Ubuntu/linux.  Am using Ubuntu 12.  Before this I lost the software center and all my mail settings and re-installed.  The Ubuntu experience is losing its novelty.

---

### Post by oldfred on 2012-05-20
Just getting grub> says something is wrong in booting. But your other issues are totally different and I am not familiar with them. Are you installing software from other than Ubuntu?

To see the entire boot configuration run this and the BootInfo and post link to the report it creates.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report & post the link it creates, so we can see your exact configuration.

---

### Post by MC Fox on 2012-05-20
I made the repair disc.  I put the dvd player at the top of the boot list but the laptop will not boot from the disk.  
I downloaded Ubuntu straight from the Ubuntu website.  
I don't know how to access 'Create BootInfo'. 
I don't know to reach command lines to modify lines.
I have an acer 5100 with Vista if that makes a difference.

---

### Post by oldfred on 2012-05-20
Are you burning the CD not just copying the ISO to the CD?

Also instructions for CD or USB
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Unless CD/DVD is bootable, the computer will not boot from it. But you do not just copy ISO as one large file to CD, but install or burn it, so it creates the boot info and many files to use to boot.

---

### Post by MC Fox on 2012-05-20
Thanks.  I'll work on it.

---

### Post by MC Fox on 2012-05-26
I burned the boot fixer CD.  Didn't work.  I was amused when instructed to backup data and activate the internet connection.  Tough to do when the operating system won't operate.  I ordered some disks.  Maybe those will work.  I may try one of the other suggestions too.  I get tired of reinstalling Ubuntu every two days.

---

### Post by oldfred on 2012-05-26
The liveCD should also work on the Internet.

Are you dual booting with Windows and have DRM software that overwrites grub2 code in the boot area just after the MBR, but before the first partition. Grub & some Windows software are not compatible. Some other HP or Dell utilities also do the same thing and most just uninstall those as they really do not do much.

---

### Post by YannBuntu on 2012-05-26
Hello

> **MC Fox said:**
> I burned the boot fixer CD.  Didn't work.  I was amused when instructed to backup data and activate the internet connection.  Tough to do when the operating system won't operate.

If you were asked to connect internet just after clicking on the "Recommended repair" button, that means that your GRUB needs a purge.
If you are not familiar with the Debian connection manager (Boot-Repair-Disk is based on Debian-live), or if you use Wifi, please don't use Boot-Repair-Disk, but instead either:
- run Boot-Repair from [this disk]("https://help.ubuntu.com/community/UbuntuSecureRemix")
- [install then run Boot-Repair from a Ubuntu live-CD]("https://help.ubuntu.com/community/Boot-Repair#A2nd_option_:_install_Boot-Repair_in_Ubuntu")

---

### Post by MC Fox on 2012-05-27
Thanks.  I'll give it a try.  I do have Vista :>( installed also.
Logic tells me upgrading to Windows 7 would not effect Ubuntu.  But...what do you think?

---

### Post by oldfred on 2012-05-27
Boot-Repair should work.

But after any Windows install or repair, it will install its boot loader and you have to reinstall grub2's boot loader. Again boot repair will work, or you can use liveCD to repair grub2. 

Always best to have at least one repairCD or liveCD for the current version of each operating system installed.

If Boot-Repair does not work for any reason, this has instructions to use command line on liveCD.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10 - grub2) - talsemgeest
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
Reinstall grub2 - Short version & full chroot version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by MC Fox on 2012-06-01
Been using the 12.04 remix for several days and no"grub" issues.  Thanks to all who replied.  I am looking forward to becoming one with Ubuntu.  I am learning alot about computer science with "Easy" Ubuntu.

---

