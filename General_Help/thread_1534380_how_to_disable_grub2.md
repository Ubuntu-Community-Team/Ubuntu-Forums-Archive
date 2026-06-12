---
title: "how to disable grub2"
date: 2010-07-19
forum: General Help
---

### Post by PerryCarvish on 2010-07-19
After the nightmare of installing Ubuntu10.04 as my second os, with windows 7, dual booting using grub 2 ( GRUB PUTS NOT FOUND). I am using wubi and the win 7 bootloader, I still have the splash screen of grub 2 after I select Ubuntu off the win7 boot loader. I really don't think I need this. Could I get rid of the grub 2 loader, it really doesn't serve any purpose except take up boot up time? go easy, it took me a while to figure out how to shorten the DEFAULT boot load time in grub 2

---

### Post by cariboo on 2010-07-19
You should be able to remove grub2 from the mbr using your Windows 7 install CD. Use the repair function.

---

### Post by bcbc on 2010-07-19
> **PerryCarvish said:**
> After the nightmare of installing Ubuntu10.04 as my second os, with windows 7, dual booting using grub 2 ( GRUB PUTS NOT FOUND). I am using wubi and the win 7 bootloader, I still have the splash screen of grub 2 after I select Ubuntu off the win7 boot loader. I really don't think I need this. Could I get rid of the grub 2 loader, it really doesn't serve any purpose except take up boot up time? go easy, it took me a while to figure out how to shorten the DEFAULT boot load time in grub 2

This guide explains how to prevent the grub menu from showing: [http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:hide_menu:)

---

