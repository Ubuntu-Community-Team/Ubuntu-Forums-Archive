---
title: "2 Hard drives"
date: 2010-04-30
forum: General Help
---

### Post by bailboy91 on 2010-04-30
I'm new here obviously but not so new to linux.  
I recently was given a new SATA drive for my pc. On my old setup i had a 160g IDE hd dual booting Ubuntu 9.10 x64 and win7 x64
NOW i have win7 on the new SATA drive and i put Ubuntu on the old IDE and i cannot boot into linux for the life of me.  I downgraded to 9.04 to use Grub instead of Grub 2 to no avail.  I've tried editing the menu.lst file and tried messing with the windows 7 boot loader.  So what i want to know is how can i get either Win 7 bootloader or Grub to see both operation systems on both drives and be able to select which os to boot into.  

Thank you in advance

-Bailboy91

---

### Post by limey_rick on 2010-04-30
Can you provide a bit more information on the problem?

Ubuntu is installed on the IDE - what is the BIOS disk that should boot first? When you installed Ubuntu, did GRUB install on the first BIOS disk?

What do you see when you actually boot the PC? Do you see GRUB menu, but when you select Ubuntu it does not work, or do you not actually see the GRUB menu?

---

### Post by IamPi on 2010-04-30
easiest way is have windows  7 setup then install ubuntu. Then download easybsd for windows and edit the windows 7 boot menu.

---

