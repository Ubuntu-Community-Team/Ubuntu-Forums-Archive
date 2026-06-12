---
title: "PLEASE HELP!!!  Failed install of 10.04 on netbook"
date: 2011-12-19
forum: General Help
---

### Post by Zenrunner92 on 2011-12-19
I can't believe it...I've successfully installed 10.04 from an Ubuntu CD on 3 different friends' laptops, and today seems to be a total disaster:

After the install completed, Ubuntu ejected the CD from the external DVD drive and prompted me to restart.  But now every time I restart, I am only getting the OEM splash page ("Lenovo") which stays on for about 3 seconds, then black screen, then flashes back on...an infinite loop!

If it were my own machine, I would happily reinstall Ubuntu as a single boot OS, but my friend just wanted to have both Win7 and Ubuntu side by side.  

Stupidly, I did not make a Win7 recovery CD first.

What, if any are my options???

I don't want to sour him completely on Ubuntu...was enjoying my newfound vocation as an Ubuntu missionary!

](*,)](*,)](*,)

---

### Post by BC59 on 2011-12-19
Look [here]("http://http://ubuntuforums.org/showthread.php?t=1613132") if you belong to this category.

---

### Post by Zenrunner92 on 2011-12-19
^ I don't think I do fall in that category, because when I turn on the machine (Lenovo s205) I don't even get to the screen where I could choose whether to use Ubuntu or Win7.

---

### Post by MartijnNL on 2011-12-19
Not the first solution but the Tech Specs of the s205 say:

> &#8226; Lenovo Rescue System provides OneKey&#8482; recovery and OneKey Antivirus without booting into Windows

Otherwise: can you look in the BIOS at the boot priority order, whether the harddisk is still listed there? (Based on [this]("https://www.youtube.com/watch?v=ij9To78Wt3w") video you probably need to hit Escape to get there.

Also: I assume you installed GRUB during the installation?

---

### Post by Zenrunner92 on 2011-12-19
> **MartijnNL said:**
> Not the first solution but the Tech Specs of the s205 say:



Otherwise: can you look in the BIOS at the boot priority order, whether the harddisk is still listed there? (Based on [this]("https://www.youtube.com/watch?v=ij9To78Wt3w") video you probably need to hit Escape to get there.

Also: I assume you installed GRUB during the installation?

Uh-oh, I am not sure if One Key was one of the Lenovo utilities I removed when he first got the netbook.  

The F2 key still works to get me into BIOS and yes the HDD is still listed there.

I'm assuming that GRUB was installed, because I did the automatic default install which seemed to go off without a hitch.  I am not sure how I would be able to access it if I can't even get past the Lenovo boot screen though...  :confused:

---

### Post by MartijnNL on 2011-12-20
Try pressing and holding shift right after the screen turns black, this would normally get you the GRUB menu.

If you get a menu, try the recovery mode and check if you see any error while the system boots (if it does).

If you don't get GRUB you might either be missing GRUB in the Master Boot Record or perhaps you have a hardware issue.

You could try booting from a SuperGrub2 Disk: [http://www.supergrubdisk.org/super-grub2-disk/](http://www.supergrubdisk.org/super-grub2-disk/) to see if that works. If it does, try reinstalling GRUB. (Open a terminal and run: ```
sudo grub-install /dev/sda
``` (This assumes there's only one disk and it's called sda. You might want to check first by running: ```
sudo fdisk -l
``` Do not install it on a partition (like /dev/sda1)!

---

### Post by Zenrunner92 on 2011-12-24
Thanks for your help, Martin...got a little buried in work so didn't get a chance to work much on this problem the last few days.  Anyway, after much googling, I finally figured out how to activate the One Key Recovery feature (damn, this is a really nifty feature to have on a PC!) and have since restored the original Win7 configuration.

I will not attempt to reinstall Ubuntu in any dual-boot configs for any more current day PCs.  All my previous dual-boot configs that worked were with PCs 2-3 years or older...maybe the 10.04 version of Ubuntu is not totally up to date with brand new models?  (I hated the Unity desktop when I tried 11.04 on my netbook though, went back to 10.04 pronto.)

---

