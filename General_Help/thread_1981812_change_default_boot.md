---
title: "change default boot"
date: 2012-05-17
forum: General Help
---

### Post by c2tarun on 2012-05-17
Hi friends
I have Ubuntu 12.04 installed on my machine. I installed Kubuntu 12.04 on separate partition. By default now boot is controlled from kubuntu partition. In case I want to format that partition and use it I cannot.
Is there anyway to make my Ubuntu's grub as default grub??

---

### Post by dabl on 2012-05-17
Each time you install a new distribution, it will ask to install Grub, and it will default to installation on the MBR of the applicable hard drive.  If you say "OK", then you will have this problem.  What you need to do (to "chain boot" the new OS), is to set it to install to the root partition where the new Linux distribution was installed.  Or you can skip installing grub and after rebooting the original OS you can run update-grub which will let the os-prober find the new OS.

To fix the problem that you have now, you need to boot a *buntu live CD and re-install grub.

Probably the first thing to do is study up on grub and learn how to install it from a booted Live CD:

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

also see Section 4 here:  [http://www.kubuntuforums.net/showthread.php?43221-GRUB-2-A-Guide-for-Users](http://www.kubuntuforums.net/showthread.php?43221-GRUB-2-A-Guide-for-Users)

---

### Post by praveenthivari on 2012-05-17
The solution is very simple. 
Just boot into Ubuntu, and completely remove grub-pc (Select remove completely while uninstalling)
Now reinstall grub-pc. It should ask where you want to install grub. Just select where you want to install and done.

---

### Post by drs305 on 2012-05-17
It can be even easier. As long as your Ubuntu installation is untouched, just boot into it and then run 
```
sudo grub-install /dev/sda
sudo update-grub

```
That will put Ubuntu's grub back in control. Running update-grub makes sure it knows what's on your system, since it may not yet know about your other OS.

If you don't want GRUB writing to the first drive (sda) change it to the one you want.

---

