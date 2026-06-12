---
title: "adding 2nd Win7 hdd to a working ubuntu machine for dual boot"
date: 2011-07-25
forum: General Help
---

### Post by Dennis G Irwin on 2011-07-25
How do I add a win7 hard drive to a ubuntu 10.4  machine already running ubuntu, for dual boot? I really don't want to reinstall either one, so how do I fix grub to give Me a choice of OS's to boot up without using f12 key to choose boot order everytime ? , which works ok right now. I've done dual boots before, with both hdd's installed by installing winXp first then ubuntu, works fine in this order(winXp 1st then ubuntu ) because windows rewrites the boot order leaving ubuntu  out of the mix. And even on the same hdd with partitions ,but can I add a hdd?.  I removed linux hdd first then installed another hdd, installed win7, then replaced linux hdd. Both boot ok,but only by using the F12 key at start up and choosing a hdd to boot first. Please Help.

---

### Post by Quackers on 2011-07-25
Welcome to UF.
Are both drives internal or is one a USB HDD?

---

### Post by Dennis G Irwin on 2011-07-25
internal hdd's

---

### Post by Quackers on 2011-07-25
Ok thanks.
Add the Windows HDD but make sure your bios is set so that the Ubuntu drive appears in the boot order before the Windows drive. Don't use the F12 key for this, go into the bios properly and set it up then save the settings so they become permanent.
Once that is done reboot and Ubuntu should boot. Once in Ubuntu open a terminal and run ```
sudo update-grub
``` and watch as grub.cfg is run. You should see the Windows Loader recognised n the second drive. If it is, reboot and you should get a grub menu with the option of which system to boot. Try the Windows option to make sure it works.

This way the mbr of the Windows drive is untouched by grub, and if the Ubuntu drive is ever taken out the Windows drive should still boot Windows.

---

### Post by Dennis G Irwin on 2011-07-25
I was thinking that would be the case, but wanted to make sure first.. Thanks a lot for Your help, I appreciate it. I will try that and let you know the results.   Thanks again.

---

### Post by Quackers on 2011-07-25
Ok, good luck.

---

### Post by Mark Phelps on 2011-07-25
If your other drive came with a Win7 version pre-installed, it's likely to have TWO partitions containing different pieces of Win7: One will have the boot loader files, the other will have the OS and the other files.

GRUB sometimes gets confused and not only adds both to the menu, it also names them wrong.  So, if you end up with two Windows 7 Loader ... entries, you may need to try them both.

---

