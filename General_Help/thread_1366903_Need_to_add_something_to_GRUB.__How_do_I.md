---
title: "Need to add something to GRUB.  How do I?"
date: 2009-12-28
forum: General Help
---

### Post by luxinterior on 2009-12-28
ok here is my problem i have an Everex stepnote laptop ok and well i figured out how to install ubuntu( u need to add sdhci.blacklist=yes sdhci_pci.blacklist=yes to the boot) ok anyways, my question is how do i add that command to the boot cuz it always hangs up on that i cant even boot in to ubuntu , 

any info on how to fix this would be great thank you tyler

---

### Post by plusnplus on 2009-12-28
Hi luxinterior,
If you can not boot using ubuntu cd, maybe your ubuntu cd is spoil.
try in other computer to make sure the cd is working condition.

---

### Post by luxinterior on 2009-12-29
yes i can boot in to the live cd and i installed ubuntu what i want to know is how to shut off sdhci so i can just boot in to the gui because it gets hung p on the sdhci

---

### Post by wojox on 2009-12-29
GRUB2 (karmic) default kernel boot parameters go in /etc/default/grub, specifically in 'GRUB_CMDLINE_LINUX_DEFAULT'. Editing this file should be followed by a 'sudo update-grub'.

---

### Post by Sef on 2009-12-29
What version of Ubuntu are you using?

---

### Post by luxinterior on 2009-12-29
i am using 9.04

---

