---
title: "Problems with an install"
date: 2010-08-30
forum: General Help
---

### Post by emtiv334 on 2010-08-30
Hello,

I have a problem that I hope someone can help me with.  I have an Acer Aspire One that runs Windows XP.  I downloaded both the full Ubuntu (latest version but can't remember the number) and the Ubuntu for netbooks- each on a separate flash drive.  I thought I had the netbook version in my Acer when I booted it up, but I saw it was booting the full Ubuntu version.  Instead of allowing it to finish installing to run from the flash drive, I stupidly shut it down and removed the flash drive.  Ever since then, when I try to boot my Acer, all I get is the black screen of death.  I've tried the flashit.exe to flash the BIOS, but no luck.  So, I'm guessing it's not a BIOS issue.  Anybody have any suggestions on how to fix it?  I'd like to not lose anything from my hard drive.

Thanks!
emtiv334

---

### Post by lmarmisa on 2010-08-30
I recommend you to repair the loader of the Master Boot Record of your hard drive. After that, you will be able to run your XP system.

Start your system from an Ubuntu Live CD, open a terminal and type this command:

> 
sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda
Then reboot the system extracting the Live CD. Windows XP will start normally.

---

