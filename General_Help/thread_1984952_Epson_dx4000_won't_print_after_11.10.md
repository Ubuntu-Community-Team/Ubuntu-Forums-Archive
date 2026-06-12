---
title: "Epson dx4000 won't print after 11.10"
date: 2012-05-22
forum: General Help
---

### Post by Smallermike on 2012-05-22
AMD Phenom(tm) II X4 965 Processor × 4
8Gb memory
Ubuntu 11.10 64 bit, fully up to date



My Epson Stylus DX4000 will not print after updates to 11.10. The files are sent (or were) to the spool queue, but the printer is not recognised. I tried installing Foomatic, and now if I try to open "printers" in the system settings, I get a message "Failed to execute child process "su-to-root" (No such file or directory)". Previously, the printer was present with the green selected tick, but all the options I got was to list the authorised users (empty- no athorised users?) All this happened after the inks were allowed to run out in the printer, so I put in new cartridges, and the red ink light is now off. The printer works fine for copying, so it isn't broke. CUPS is installed. I've downloaded the latest drivers from Epson and installed them using the software centre, but no change. What have I done, and how do I fix it? I can do command line, but am no expert in Linux.

---

### Post by Smallermike on 2012-05-23
So, I uninstalled Foomatic, CUPS and the printer utility, rebooted, reinstalled CUPS and the printer utility, rebooted, and I'm back to a stable situation. I can see the printer in the "Printers" function in system tools/system settings, and I can then access the printer utility. If I try to print to it, the file is just held in pending status in the queue. I can still use the printer to copy documents and photos, but nothing from the PC. Please don't say I'm back to handwriting, I'm not sure I remember how.

---

### Post by Smallermike on 2012-05-23
I just tried to print using VirtualBox and Windows XP Pro x64, and it works perfectly. Have I got a conflict between the main Linux system and VirtualBox/WinXP? The printer is named the same in both systems. Could this cause a conflict? They both worked OK until the last month.

---

