---
title: "Ubuntu keeps freezing"
date: 2009-08-30
forum: General Help
---

### Post by davbeck on 2009-08-30
Ubuntu 8.10 keeps freezing. A lot of the time I am not even doing anything, it is just sitting there showing the desktop. Then it freezes and I can't do anything with either the keyboard or the mouse. Network functions (on other computers) become unavailable as well so I don't think it is the screen that is freezing. It happens about every 10 minutes. The caps lock and scroll lock lights on the keyboard also start blinking.

---

### Post by filip007 on 2009-08-30
Try 9.04 or maybe is hardware problem or try Memory test on Ubuntu boot cd menu.

---

### Post by davbeck on 2009-08-30
I had the same problem on 9.04. I downgraded to resolve an issue with the internet.

---

### Post by filip007 on 2009-08-30
What's your sys..

---

### Post by davbeck on 2009-08-30
It's a Dell Dimension 3000 with an Nvidia GeForce MX 4000.

---

### Post by Liolikas on 2009-08-30
Try to grab **dmesg** commend output after freeze maybe login over ssh to your box still work? It may help alot to track down problem.

---

### Post by davbeck on 2009-08-30
Network functions are also unavailable when it freezes.

---

### Post by Liolikas on 2009-08-30
Then all I can suggest is download 9.04 from ubuntu.com

---

### Post by P4man on 2009-08-30
> **davbeck said:**
> The caps lock and scroll lock lights on the keyboard also start blinking.

You got a so called "kernel panic". These can be a pain to troubleshoot, but usually result from a problem with the BIOS, more specificially, ACPI.

You should check your log files for clues. If you go in system > administation > log file viewer, see if you can find anything around the time the freeze happened. if you see something, post it here.

You should also check if there is a newer bios available for your computer, and update it if possible.

You can also try disabling a few things in the kernel. when you boot, press escape to enter grub menu. Select the top ubuntu line, and press E to edit. Select the kernel line, press E to edit. Then add a kernel switch at the end of the line. Try this "nuclear" option:

acpi=off

It will disable a lot of powermanagement options, and it may even not boot, but its worth trying if it solves the freezing. Any change you make there only lasts 1 boot. upon rebooting, it will use default settings again.

Other things you can test:

[https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options](https://help.ubuntu.com/community/BootOptions#Common%20Boot%20Options)

more info on setting kernel parameters:

[https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation](https://help.ubuntu.com/community/BootOptions#Change%20Boot%20Options%20Temporarily%20For%20An%20Existing%20Installation)

---

### Post by filip007 on 2009-08-31
Your sys is then...
2.66GHz Intel Celeron D 330; Intel 865G chipset; 512MB DDR SDRAM 400MHz; 96MB (shared memory) integrated Intel 865G; Seagate ST340014A 40GB 7,200rpm

and you added Geforce MX4000 that's Geforce 2 MX very old, get it out and try onboard display or add something newer like Radeon X1600 is for AGP.
I hope you got AGP or you're running PCI display.

---

