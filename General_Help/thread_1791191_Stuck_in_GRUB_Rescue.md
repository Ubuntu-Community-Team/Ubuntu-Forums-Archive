---
title: "Stuck in GRUB Rescue"
date: 2011-06-26
forum: General Help
---

### Post by marclane on 2011-06-26
Hey,

So I'm an Ubuntu Noob. I have a Asus Netbook (not preinstalled with ubuntu). I had a dual boot windows 7 home premium and ubuntu 10.10. I wanted to update to ubuntu 11.04, but the update went wrong and ubuntu stopped working.

Fair enough, it happens.

So I booted into windows and removed the linux partition. BUT I FORGOT TO REMOVE THE GRUB. Now I can't boot into Windows at all, because it's stuck in GRUB rescue.

Since it's a netbook, it doesn't have a cd drive. What should I do? I don't want to reinstall/format windows (it's a work computer, so I have a lot of important files on there), and the computer didn't come with recovery software. How can I solve this problem? Can it be removed via a live boot of ubuntu?

Please give me step my step instructions... I really don't know much about using the terminal or command line

UPDATE

So got my hand on a live USB of Ubuntu, but even though I set boot priority to USB, it still defaults to grub rescue. What to do?

thanks

---

### Post by Bnelsonmiller on 2011-06-26
Im having the same problem. I have a windows recovery .iso, but it won't boot from the usb.

Any help?

---

### Post by Ozymandias_117 on 2011-06-26
If you're going back to the grub rescue screen, it isn't properly booting from the USB.  If you're certain the computer is set to boot from USB first, are you certain the live USB was written to the drive correctly?

Edit: I guess I didn't fully answer your question.  After removing the windows boot loader, it's gone.  If you want to get rid of ubuntu, and don't have a recovery CD for windows, your best bet is to reinstall ubuntu, boot to Windows, and try out EasyBCD: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

It says it's able to reinstall a Windows boot loader.  After that you can delete the Ubuntu partition again.

---

### Post by garvinrick4 on 2011-06-26
If you have a Live USB of Ubuntu and do not have any USB device for Windows to reinstall
Windows bootloader then use the Live USB of Ubuntu choose Try UBUNTU and when it
boots make sure internet is working and then open a terminal and copy and paste these
will give you a bootloader called "Lilo" that will boot Windows for you.
Restore basic windows boot loader - universe enabled 
```
sudo apt-get install lilo
```
```
sudo lilo -M /dev/sda mbr
```
May show error messages about the rest of lilo missing, ignore, we just want MBR
Now reboot into Hard Disk Drive and Windows should boot.

---

### Post by varunendra on 2011-06-27
> **Ozymandias_117 said:**
> After removing the windows boot loader, it's gone.  If you want to get rid of ubuntu, and don't have a recovery CD for windows, your best bet is to reinstall ubuntu, boot to Windows, and try out EasyBCD: [http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

It says it's able to reinstall a Windows boot loader.  After that you can delete the Ubuntu partition again.
+1
It's a sure-shot way IF EasyBCD can reinstall Win7 boot loader.

> **garvinrick4 said:**
> .... will give you a bootloader called "Lilo" that will boot Windows for you....
I'm suspicious about lilo being able to boot Win7. It certainly can boot XP or earlier versions, but Vista and Win7 have different and a bit complex booting process. But since it is a very quick method and doesn't touch anything except MBR, I think it won't hurt trying it first.

@marclane,
Please inform us here what worked for you and how.

---

