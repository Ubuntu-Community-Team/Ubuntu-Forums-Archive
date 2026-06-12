---
title: "Need help removing menu items from grub 2"
date: 2010-08-19
forum: General Help
---

### Post by aviramof on 2010-08-19
When i reinstalled Ubuntu i reinstall it on top of an existing not working ubuntu so now
in the boot menu i still have 2.6.35-6-generic menu items but i can't find 2.6.35-6-generic
anywhere how can i fix it?

Thanks in advance.

---

### Post by Rubi1200 on 2010-08-19
Hi,
I am not sure I understand the last part of your post:

> but i can't find 2.6.35-6-generic anywhere

What is the current kernel version(s) you have in the GRUB menu?

To remove extra entries from the GRUB menu, such as different kernel versions, go to Synaptic and search for linux-image and linux-headers. There will be 3 files to remove for each kernel version.

By the way, in most cases it is advisable to keep at least 1 extra entry as a spare in case something went wrong during an upgrade.

Also, you might want to try running 
```
sudo update-grub
``` in the terminal

Hope this helps.

:-)

---

### Post by Yarui on 2010-08-19
My method for only having the current kernel version in my grub menu is to navigate to the /boot directory and move all of the older kernel files (all of the files that have the numbers of older versions in the file name) into their own folder and then run update-grub from the terminal.  I use /boot/oldkernels/kernelversion.

I do this because it is best to keep older kernels on your system in case you need to fall back on them for troubleshooting, but update-grub always adds all of the kernel versions in your /boot folder to the grub menu.  This is the simplest fix I have found for this issue so far.

If you don't find older versions of the kernel in your /boot directory, running update-grub in your terminal should get rid of the menu item.

---

### Post by oldfred on 2010-08-19
You can customize it if you want:

Total Custom menu:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)
[http://ubuntuforums.org/showthread.php?t=1483827](http://ubuntuforums.org/showthread.php?t=1483827)

How to: Create a Customized GRUB2 Screen that is Maintenance Free. 
[http://ubuntuforums.org/showthread.php?t=1542338](http://ubuntuforums.org/showthread.php?t=1542338)

OR Partial Custom, similar to above post:
I used drs305's command to limit ubuntu entries to two, turned off os_prober so it does not look for other systems and totally customized my 40_custom.
includes line to limit display to two, also hiding of windows recovery partition
Grub 2 Title Tweaks Thread -drs305
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)
In /etc/default/grub I added this:
gksudo gedit /etc/default/grub
GRUB_DISABLE_OS_PROBER=true
or
sudo chmod a-x /etc/grub.d/30_os-prober

---

### Post by aviramof on 2010-08-19
> **Yarui said:**
> My method for only having the current kernel version in my grub menu is to navigate to the /boot directory and move all of the older kernel files 

Thanks i deleted all older kernels from there and that it and by the way synaptic didn't showed them because the reinstall ubuntu without format.

---

