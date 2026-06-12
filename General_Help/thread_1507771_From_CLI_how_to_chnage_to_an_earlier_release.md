---
title: "From CLI how to chnage to an earlier release"
date: 2010-06-12
forum: General Help
---

### Post by speed32219 on 2010-06-12
I currently am running  (Karmic) linux-2.6.31-20 on one machine and linux-2.6.31-22 on another.  I just installed the newer OS a couple of days ago.  I have some applciations that run fine under 2.6.31.20 but are buggy using the newer 2.6.31.22, so I want to move revert back to the older release.  I would need to do it with the CLI, I do not have gdm installed.  

I can probably do it through aptitude, but not sure.  Can anyone explain or point me in the right direction.  In the future I will be moving to Lucid, just want the dust to settle.

---

### Post by wilee-nilee on 2010-06-12
As far as I know there is no revert option, you could install lucid along side if your using grub2 or install the one you want and drag over the stuff you want then delete the one you don't. Or just back up home and reinstall. The main thing here is to not mix grub legacy and grub2.

---

### Post by exodus_ on 2010-06-12
From what I see, you want to keep the same Ubuntu release (karmic) but you want to use an older kernel instead of the shiny new one?

If this is the case, the older kernel may still be around on the system.  When you boot it up, if you hold down shift after the POST but before Ubuntu starts loading, you should get a grub menu.  Have a look around, I think it's shift to get the menu, but I am not sure because I still use Grub legacy.

If your old kernel is listed as a boot option, all you would need to do is remove the new kernel like this:

```
sudo apt-get remove {name of kernel package}
sudo update-grub

```

If you try this, make **SURE** that you have the old kernel installed or else you will NOT be able to boot the system and it will be a little more difficult to fix. However, if you get to the grub menu and you **do not see** the old kernel listed, you will instead need to INSTALL the new kernel, and run update-grub.  It's imperative that you have at least one kernel installed, and I generally like to keep two just in case something goes wrong with one of them.

If you need any other help or clarification let me know.


P

---

### Post by speed32219 on 2010-06-12
Thank you fo the responses.

I am trying to stay with Karmic, waiting for the dust to settle on Lucid

exodus_, I installed the OS with the same cd that I had installed the original system with and it is a standalone with only one kernel.  I think the mini-iso CD is Karmic 2.6.31.14 (I have another system that is running 2.6.31.15 from the same CD)that I made many months ago, and during a preivous installation it updated during the install to 2.6.31.20.  Everything continued to work fine, I just put another machine togehter and after install it went to 2.6.31.22.  

So during the installation process it is upgrading to the latest release.  I really want either 2.6.31.xx (.15 or .20) and not .22.  I was looking into downloading the kernel headers for .20 and I have found a site that has them, but I am trying to do it with aptitude or apt-get instead of a .gz file so I can get them installed.

---

### Post by speed32219 on 2010-06-13
Turned out to be a bios problem with the Gigabyte MB and an update fixed my problem.  So 2.6.31.22 is good for me.

---

### Post by exodus_ on 2010-06-13
Hey well I am glad you managed to solve your issue!

---

