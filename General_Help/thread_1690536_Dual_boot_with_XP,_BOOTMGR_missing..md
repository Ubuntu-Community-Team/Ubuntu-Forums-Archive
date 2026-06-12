---
title: "Dual boot with XP, BOOTMGR missing."
date: 2011-02-18
forum: General Help
---

### Post by Veren on 2011-02-18
Hello, I have an Asus EEE (it has no cd drive) and I've been using Ubuntu as my primary system. I was thinking about installing Windows XP though flash drive, so that I can dump Wine.
I formatted the flash to ntfs, flagged it as boot and extracted the cd's iso there. Reboot, changed priorities in BIOS and it keeps saying "Missing BOOTMGR, press ctrl+alt+del".
Now, from my search it`s a fairly common problem, though all of the solutions just say to reinstall from a cd or recover from windows, what is of course not possible.
Do you have any idea ? Thanks. 
Do you think it's related to only this version (XP) ? Or is it global, so the same thing would happen were I to use Win 7 ? Thanks

Edit: This is stupid. From what I've read this problem is solely related to Vista/7, not to XP. Strange.

---

### Post by sikander3786 on 2011-02-18
I don't know of any method of booting XP from a USB drive. Some enthusiast might jump in and enlighten you on that.

Windows 7 comes with an official USB creation tool from Microsoft and also you can prepare a Windows 7 USB from Ubuntu.

If you want to run Windows XP, you can run it inside your Ubuntu install using VirtualBox and it would run all of your Windows software. Games won't work as there would be little or no 3d acceleration. See the link in my signature.

---

### Post by wilee-nilee on 2011-02-18
If you have access to a windows OS this works quite well, if the XP ISO is a legitimate MS, say a oem etc.
[http://wintoflash.com/home/en/](http://wintoflash.com/home/en/)

---

### Post by oldfred on 2011-02-18
I saved these links but never have used them.


Copy Windows XP to usb
Please note this tutorial works on all computers not just the Asus EEE PC.
[http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html](http://www.eeeguides.com/2007/11/installing-windows-xp-from-usb-thumb.html)
USB install of XP
[http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html](http://komku.blogspot.com/2008/11/install-windows-xp-using-usb-flash-disk.html)

---

### Post by Veren on 2011-02-18
Thanks for advices, though I'm afraid that won' help me, because:
those programs are .exe (maybe I could run those in VirtualBox ?), but the thing is that I have no Windows installed at the moment. I've never used VirtualBox to be honest, though I used to use Wine quite a lot. Also, could you tell me what program you can create live Win7 USB in in Ubuntu ? Also, I still wonder why it keeps talking about BOOTMGR when that has nothing to do with XP, it should be NTLDR...

---

### Post by Veren on 2011-02-18
Yeah, and the 3D accelaration is pretty much what matters, I can't find what else is Windows good for :D so the VirtualBox a no-go.

---

### Post by sikander3786 on 2011-02-18
Creating Windows 7 USB is easy in Ubuntu. See here.

[http://ubuntuforums.org/showpost.php?p=9458199&postcount=6](http://ubuntuforums.org/showpost.php?p=9458199&postcount=6)

---

### Post by Veren on 2011-02-18
> **sikander3786 said:**
> Creating Windows 7 USB is easy in Ubuntu. See here.

[http://ubuntuforums.org/showpost.php?p=9458199&postcount=6](http://ubuntuforums.org/showpost.php?p=9458199&postcount=6)

Thanks, though that is exectly what I did with XP :) I hope to have more luck with 7.

---

### Post by sikander3786 on 2011-02-18
> **Veren said:**
> Thanks, though that is exectly what I did with XP :) I hope to have more luck with 7.
Windows 7 was intended to boot from a USB Drive so I think it would work.

Just posted it to my blog with screen shots. See for a reference...

[http://ubuntu4beginners.blogspot.com/2011/02/create-windows-7-startup-usb-from.html](http://ubuntu4beginners.blogspot.com/2011/02/create-windows-7-startup-usb-from.html)

---

### Post by Veren on 2011-02-18
> **sikander3786 said:**
> Windows 7 was intended to boot from a USB Drive so I think it would work.

Just posted it to my blog with screen shots. See for a reference...

[http://ubuntu4beginners.blogspot.com/2011/02/create-windows-7-startup-usb-from.html](http://ubuntu4beginners.blogspot.com/2011/02/create-windows-7-startup-usb-from.html)

Thank you very much, but I'm afraid I'm gonna work on it in the morning, it's getting rather late. I'm sure to check it :P

---

