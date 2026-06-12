---
title: "GRUB/BURG Entry Delete?"
date: 2011-01-22
forum: General Help
---

### Post by helios16v on 2011-01-22
I just finished my Windows 7 install then dual booted with Ubuntu 10.10.
I didn't like the look of GRUB so I installed BURG for some graphical interface but I didn't really think that it's going to give an entry for every boot there was on the GRUB menu..

When I start up there are 6 different boot options for Ubuntu, and the 7th is Windows 7.

How do I remove everything off of that menu except for the primary Ubuntu kernal and Windows 7?

I only want two selections for Ubuntu 10.10 and Windows 7 in BURG.

-Ben

---

### Post by drs305 on 2011-01-22
The six Ubuntu options are probably 3 kernels and their recovery modes. I won't speak for how BURG does things, but you can probably reduce the number of Ubuntu entries by removing one or both of the older kernels. Most users keep at least one backup kernel in case the newer one fails.

There should also be a menu entry to turn off the recovery mode. In Grub2, the setting is in /etc/default/grub and you remove the # icon from the disable recovery mode line. BURG probably has something similar.

Once kernels are removed from the system they usually disappear from the menu as well once it is updated. To remove older kernels, here is a guide that tells you how to easily accomplish it with Ubuntu Tweak:
[HOWTO: Remove Older Kernels via GUI]("http://ubuntuforums.org/showthread.php?t=1587462")

---

### Post by helios16v on 2011-01-22
Thanks, there was a link in the link you posted which lead me towards "GRUB Customizer" [http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

Installed that via terminal, when I opened it, the program recognized I was using BURG and I simply unchecked the boxes for each kernal and recovery modes I didn't want to show up and now it works perfect.

Thanks for the help.

Only problem now is there is no more Ubuntu loading splash, just a flashing underscore.

-Ben

---

### Post by stinkeye on 2011-01-23
> **helios16v said:**
> Only problem now is there is no more Ubuntu loading splash, just a flashing underscore.

-Ben
This is a fix for Plymouth showing text instead of logo.
Not sure if that's your problem
but it won't hurt to try. 
Open grub-customizer in burg mode.
Go to Edit > preferences > advanced 
and enable or add the entry
```
GRUB_GFXPAYLOAD_LINUX
```
using your desktop resolution. eg **1680x1050**
The actual line in /etc/default/burg will look like
```
GRUB_GFXPAYLOAD_LINUX="1680x1050"
```




This is a fix for only seeing Plymouth briefly.
gksudo gedit /etc/initramfs-tools/conf.d/splash
and add this option 
```
FRAMEBUFFER=y
```
save the file.


Then
```
sudo update-initramfs -u
```

---

### Post by nzjethro on 2011-05-26
For a simple fix, press 'f' when the burg screen is showing. It "folds" all of the duplicate entries, so you end up with just Ubuntu and Win (or whatever your OSs are). Plus, saves the hassle of going through config settings.

---

### Post by Paschalis89 on 2011-10-30
> **nzjethro said:**
> For a simple fix, press 'f' when the burg screen is showing. It "folds" all of the duplicate entries, so you end up with just Ubuntu and Win (or whatever your OSs are). Plus, saves the hassle of going through config settings.

after install grub modifier, i saw this.

thanks.

Much easier, not to mess with bootloader entries in case that you upgrade and newer versions dont work:popcorn:

---

