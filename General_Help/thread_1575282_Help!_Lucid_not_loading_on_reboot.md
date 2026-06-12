---
title: "Help! Lucid not loading on reboot"
date: 2010-09-15
forum: General Help
---

### Post by npattillo on 2010-09-15
Help! I run a dual boot Windows / Lucid on my Acer Aspire 5740-6378 laptop. I was trying to fix a problem with my backlight per a help forum on the subject and I screwed up a boot command. I rebooted and the purple Ubuntu screen goes to boxes and a black screen with only my number lock light flashing. I looked under the edit command option at boot up and this is the code that I get;
 
linux/boot/vmlinuz-2.6.32-24-Generic root= uuid=f8430443-1824-4965-9\1c8-2760449428b3 ro no modeset acpi_backlight=vendor quiet splash\ac pi_osi=Linux
 
I know that this is the problem, because I recognize the code that I entered. I would love to continue to use Ubuntu, so please help me figure out what I need to do on a command line when I boot up to fix it. Thanks!!!

---

### Post by arrange on 2010-09-15
Can you post the output of the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)

---

### Post by JK3mp on 2010-09-15
Change "no modeset" to "nomodeset"

---

### Post by npattillo on 2010-09-15
> **arrange said:**
> Can you post the output of the [boot_info_script]("https://sourceforge.net/projects/bootinfoscript/")? (If you don't know how to run the script, [look here]("http://bootinfoscript.sourceforge.net/").)
 
I cannot get Ubuntu to run, so I cannot open terminal. Can I do so in a command line at boot up?

---

### Post by npattillo on 2010-09-15
I just got it to boot up by editing the grub line at boot up. I went back into gedit and erased the stuff that I put in there earlier, saved and reloaded:D. I hope it won't ever happen again.

---

