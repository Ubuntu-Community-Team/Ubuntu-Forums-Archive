---
title: "Cannot boot into XP on other HDD"
date: 2010-07-07
forum: General Help
---

### Post by uRabbit on 2010-07-07
Hard to sum up in the title, so here it is:

I have Ubuntu 10.04 LTS installed on my 250GB external. I have XP already installed on my 500GB internal. But, for some reason, I cannot boot into XP (the default) without going to the BOOT MENU, selecting USB HDD and then selecting XP. But XP is not on the external USB HDD. Only Ubuntu. 

Also, for some reason, the 250GB is not showing up in Ubuntu. It did on the first three boots...
edit: NVM, I think the 250 is labeled as File System.

---

### Post by oldfred on 2010-07-08
this link, I think is about your problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

Basically you want grub2 installed to the MBR of the external and BIOS set to boot the external first. Then reinstall a windows boot loader to the internal, so if no external found it boots directly to windows.

---

### Post by uRabbit on 2010-07-08
> **oldfred said:**
> this link, I think is about your problem:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Computer_does_not_boot_without_external_drive)

Basically you want grub2 installed to the MBR of the external and BIOS set to boot the external first. Then reinstall a windows boot loader to the internal, so if no external found it boots directly to windows.

That sounds exactly like what's going on. Awesome, I'll give that a shot tomorrow. :)

Thank you.

---

### Post by uRabbit on 2010-07-09
Okay, so now when I try to load Ubuntu, it loads grub instead. What do I do there?

---

### Post by oldfred on 2010-07-09
It is supposed to load grub to get to Ubuntu. Do you not get a grub menu. then you have a grub error. What exactly is on your screen? Some just require manual booting, others reinstall of grub. 

To see what is where, with external plugged in:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Paste results.txt, then highlight entire file and click on # in edit panel(code tags) to make it easier to read.

---

