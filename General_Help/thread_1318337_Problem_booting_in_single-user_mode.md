---
title: "Problem booting in single-user mode"
date: 2009-11-07
forum: General Help
---

### Post by sschafer on 2009-11-07
Short version: When I boot into recovery mode in the latest kernel in Ubuntu 9.10, the display and keyboard get messed up so that I can't type any commands.      

Longer version:  After a bunch of boot messages it clears the screen and pops up a non-GUI menu with some recovery options, but before I can do anything, it starts displaying more boot messages on top of that menu.  One of them I remember specifically is that it was shutting down NTP.  There is also several lines of garble.  After it stops, nothing I type has any effect other than control-alt-delete, which reboots the system and control-A which appears to execute whichever menu command I happened to have selected.  After typing Control-A it may dump me to a command prompt, but it doesn't properly recognize what I type.  For example, typing "help", results in "elp" is not a valid command.    

I have found that I can get into recovery mode in an older kernel, but I'm wondering if anyone has experienced this and/or has any suggestions for workarounds or fixes.

---

### Post by sschafer on 2009-11-08
I found a workaround, in case this helps anyone:

Edit the standalone boot.  At the end of kernel boot line it has "ro single".  Change it to "single init=/bin/bash".

---

### Post by rough68fish on 2010-04-09
With 9.10 under vmware after a couple of days of using an image I can nologer login. When I do it looks like it's starting gnome (plays the little chime) and then comes back to the login page. 
 
I can't even get into single user mode at this time. When I reboot I try to press ESC at the Grub loading but I never get a menu. If I do it before I see the grub message I get the BIOS. 
 
How are you getting into sigle user / console mode?
 
--Sean

---

### Post by sisco311 on 2010-04-09
> **rough68fish said:**
> With 9.10 under vmware after a couple of days of using an image I can nologer login. When I do it looks like it's starting gnome (plays the little chime) and then comes back to the login page. 
 
I can't even get into single user mode at this time. When I reboot I try to press ESC at the Grub loading but I never get a menu. If I do it before I see the grub message I get the BIOS. 
 
How are you getting into sigle user / console mode?
 
--Sean

In Ubuntu 9.10, GRUB 2 is the default boot loader and manager. To get the boot menu to show, you have to hold down the Shift key during bootup.

---

### Post by rough68fish on 2010-04-09
> **sisco311 said:**
> In Ubuntu 9.10, GRUB 2 is the default boot loader and manager. To get the boot menu to show, you have to hold down the Shift key during bootup.
 
Thank you. I've decided until I figure out what's going on I have turned off the grub2 splash screen so I can see the system boot and have disabled gdm for runlevel 2. I'm pretty sure my problem is with x-windows starting so I start to patch and see when it breaks.
 
--Sean

---

