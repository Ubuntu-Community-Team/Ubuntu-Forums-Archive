---
title: "Slackware with Ubuntu"
date: 2009-12-31
forum: General Help
---

### Post by madmax.santana on 2009-12-31
I don't know which section would be best to put this pot in.
Has anyone ever tried Slackware and Ubuntu on the same system?
I have Windows Vista, Ubuntu and Linux Mint already on my system. I am trying new distros nowadays, just for fun. I have Slaskware on a DVD, but I wanna confirm before doing anything with my system whether it is safe and applicable or not?

---

### Post by madmax.santana on 2009-12-31
I had once tried to do the same with Fedora 12 but somehow my boot sectors got deleted. Although Vista and Fedora would boot right but Mint and Ubuntu were not running. I had to do a lot of work to get my GRUB back.

That was even as I did not permit Fedora to install its bootloader.

---

### Post by ajgreeny on 2009-12-31
There is no real reason for it to be a big problem, and I can't imagine what happened when you installed fedora, as it should have left things as they were.  I have never used slackware so don't know what grub it uses, or even if grub is its bootloader, but even if it is a problem you can get your current linux running again by restoring grub quite easily.  There are a lot of threads on how to do that here, and if you google as well.

---

### Post by Locutus_of_Borg on 2009-12-31
i endorse the installation of slackware

I have dual booted slack with ubuntu in the past

there is no conflicts between them

slackware uses lilo as the boot loader, if you wish to continue using grub, during the installation you will be asked if you want to install a boot loader, just say no at that point.  if you are using legacy grub e.g. not the grub that comes with 9.10, then you should use ext3 as the filesystem for slackware, if you want to use ext4 (recommended) then either use lilo (also recommended) or grub2 for the bootloader

it is also recommended to do a full install of slackware, though if you do not want KDE, simply unchecking the K series is enough

---

### Post by madmax.santana on 2009-12-31
Real nice explanation, guv. Thanks, got yer point. Em gonna have a go at it. Thanks for the tips! :)

---

