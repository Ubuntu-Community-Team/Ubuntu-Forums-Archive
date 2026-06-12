---
title: "Using windows boot loader to boot ubuntu"
date: 2010-02-09
forum: General Help
---

### Post by NPV1597 on 2010-02-09
Is there a way to use the default windows boot loader to boot ubuntu. I only use ubuntu to do my computer science homework, I use windows 7 for everything else. Right now grub has ubuntu set as the default OS to boot. I want my computer to boot windows 7 unless I hold F8 and select ubuntu. Is this possible to do with the windows boot loader or grub?

---

### Post by kmsalex on 2010-02-09
you could just set grub to boot win 7 by default, go to system>start up-manager, then you can set your default os in the drop down box. then you can change the time out time. so you could set it to 1 or 2 sec and win 7 as the default. not to shour about using the windows boot loader. there probably is a way but using grub has always worked fine for me.

---

### Post by Brandon Williams on 2010-02-09
If grub is already installed and working correctly to boot both ubuntu and windows, then you just need to tell grub to use windows as the default OS. [Here](https://help.ubuntu.com/community/Grub2) is a page that explains in detail how to work with grub, including how to specify the default OS.

Here's a short summary of what you need to do.

First, view /boot/grub/grub.cfg. Look for a section that starts with "BEGIN /etc/grub.d/30_os-prober". Find the exact name used in the grub menu to describe the option to boot into windows. On my system, it looks like this:
```
menuentry "Windows 7 (loader) (on /dev/sda1)" {
```

Next, use an editor to open /etc/default/grub. This will require that you use sudo, as in 'sudo gedit /etc/default/grub', because the file can only be modified by the superuser. Find the line that says 'GRUB_DEFAULT=0' and change the 0 to the label for windows that you found in the previous step. On my system, it looks like this:
```
GRUB_DEFAULT='Windows 7 (loader) (on /dev/sda1)'
```

Finally, update grub by running 'sudo update-grub'. This will update /boot/grub/grub.cfg so that the windows OS is the default option. If you want to boot into ubuntu, press the shift key when you see the word 'grub' on the screen at boot time. This will present a menu from which you can select the ubuntu option.

PS: Just saw the previous entry. Using startup manager would be easier than the manual method I described. You may have to install startup manager first.

---

### Post by sideaway on 2010-02-09
As far as I know, there is no current way to get the Windows boot loader to recognise and boot Ubuntu. Your best option is to therefore make Windows the default in GRUB and shorten the timeout time.

---

### Post by NPV1597 on 2010-02-09
thanks for the info!

---

### Post by wilee-nilee on 2010-02-09
Startup manager in synaptic will allow you to set the booting OS and the time out. You don't have to edit grub unless you want to.

---

### Post by momalle1 on 2010-02-10
You certainly can use the Windows boot loader to load Ubuntu but as already stated, just set Windows as your default if that is what you need. I use the Windows boot loader because I was having sleep/hibernation issues using GRUB. Basically, search for GRUB2 here, there are a few tutorials that will tell you how to get grub installed to your Linux partition instead of your boot sector, then restore your Windows loader using the Windows DVD, then use either EasyBCD2Beta or GRUB4DOS to add an entry to Windows' boot loader for Ubuntu.

GRUB Tips including installing it where you want it and restoring the Windows boot loader.

[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by sarin_cv on 2010-02-10
It is also possible to boot ubuntu bu editing boot.ini in windows I guess.. plz check this link

[http://ubuntuforums.org/showthread.php?p=2892604](http://ubuntuforums.org/showthread.php?p=2892604)

---

### Post by Mark Phelps on 2010-02-10
> **sarin_cv said:**
> It is also possible to boot ubuntu bu editing boot.ini in windows I guess.. plz check this link

[http://ubuntuforums.org/showthread.php?p=2892604](http://ubuntuforums.org/showthread.php?p=2892604)

Had you bothered to actually READ the op's post, you would have seen specific mention of Win7 -- which does not use boot.ini.  That was dropped back with Vista.  Win7 (as with Vista) uses an entirely different boot loader.

---

### Post by philinux on 2010-02-10
> **sideaway said:**
> As far as I know, there is no current way to get the Windows boot loader to recognise and boot Ubuntu. Your best option is to therefore make Windows the default in GRUB and shorten the timeout time.

Easybcd is what I've been using on my GF's Vista laptop, works a treat. It would work for 7 but not XP.

[http://neosmart.net/dl.php?id=1](http://neosmart.net/dl.php?id=1)

---

### Post by CS02 on 2010-09-30
> **Brandon Williams said:**
> If grub is already installed and working correctly to boot both ubuntu and windows, then you just need to tell grub to use windows as the default OS. [Here]("https://help.ubuntu.com/community/Grub2") is a page that explains in detail how to work with grub, including how to specify the default OS.

... 

PS: Just saw the previous entry. Using startup manager would be easier than the manual method I described. You may have to install startup manager first.

Thank you, Brandon. I recently change OS to using Ubuntu and didn't find startup manager under System menu --did not even know I have to download and  install it first unto my system. Now I have installed Startup Manager, but slightly before that your manual method had helped me achieve what I had wished for.  And surely a better way for me to learn Ubuntu. Really appreciate it.

---

