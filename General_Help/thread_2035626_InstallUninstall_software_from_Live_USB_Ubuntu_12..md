---
title: "Install/Uninstall software from Live USB Ubuntu 12.04"
date: 2012-07-31
forum: General Help
---

### Post by uzumakifahim on 2012-07-31
Hi,
I have installed Ubuntu 12.04 on a USB disk. Now I need to install/Uninstall some software from the USB disk. Is it possible? If so, please help me, how can I do that?

Thanks in advance.

---

### Post by GreatDanton on 2012-07-31
In the same way as if you have installed system. Click on the Ubuntu software center (in Unity looks like a shopping bag) and install the software you need.

---

### Post by uzumakifahim on 2012-07-31
Thanks for your reply. I have uninstalled a software from Ubuntu Software center, but just after that when I have rebooted my PC with that USB drive, the software is on the system. And I can use that software with all features. Would you please suggest me how can I solve that problem?

---

### Post by efflandt on 2012-07-31
In order to install software to live/install iso on USB, you need to have persistent data (casper-rw file which is actually an ext2 filesystem in a file).  You can only install things that run after booting (cannot install video drivers, kernel updates, etc.) because it initially boots a fixed squashfs filesystem before persistent data is mounted.  Persistent data can also keep certain settings, like timezone and wireless security settings.

But that fixed squashfs filesystem is likely why you cannot uninstall whatever you tried to.  It is still on the fixed squashfs filesystem that loads first, so it was not actually uninstalled.  In order to not have default programs, you would need to create your own iso first without that program(s) on it.

---

### Post by uzumakifahim on 2012-07-31
@ [efflandt]("http://ubuntuforums.org/member.php?u=937632"), Thanks for your very informative post. Could you tell me, is it possible to install the regular updates by Update Manager?

---

### Post by uzumakifahim on 2012-08-01
So, maybe it's impossible to uninstall a software from a Ubuntu installed USB stick. :(

---

### Post by efflandt on 2012-08-01
Like I said, if you have persistent data (there is a slider if you use Startup Disk Creator to create bootable live/install iso on USB), you can install additional programs.  You just cannot update or remove programs that it comes with, or that run during boot.

If you want to use special video drivers or do kernel updates and things, it would be better to do a regular install to USB.  But you would need to make sure that you put grub on the USB device.  That would take up more space than the ISO (8 GB minimum flash memory recommended), but then you could do anything you can do on a regular system, because that is what it would be.

I boot a regular Ubuntu installation from SD card (which is internally USB connected) on my tablet PC. It is not as fast as a hard drive, but works.

---

### Post by uzumakifahim on 2012-08-01
Thanks efflandt. I'm not much experienced with Ubuntu like you. But at this point could you help me that, how can I put grub on the USB device installation?

---

