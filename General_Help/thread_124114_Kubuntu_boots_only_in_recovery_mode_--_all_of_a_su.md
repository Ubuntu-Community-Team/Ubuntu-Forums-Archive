---
title: "Kubuntu boots only in recovery mode -- all of a sudden!"
date: 2006-01-31
forum: General Help
---

### Post by tinkerbell on 2006-01-31
Hi all,

So up until yesterday my Kubuntu install was working fine & had been for the last couple of months. Yesterday, a script caused Firefox to hang, my entire system froze, & in frustration I restarted by turning the power off & power back on. I rebooted in Windows, installed an update to my ATI display driver, & tried to reboot into Kubuntu.

Have been trying repeatedly, but no luck -- it goes through the boot process, reaches the stage where it says "configuring modules", loops back & begins the boot process again, & then finally reaches a root recovery prompt, saying it was unable to exit this runlevel & continue booting. The boot stage immediately preceding this is "setting up disk parameters". 

From this root prompt, if I type startx, KDE loads fine & with no problem -- except I am in recovery mode. Selecting recovery mode at boot time also leads to a smooth startup. I simply can't load the main user, i.e. me. (I have no other users set up on this machine). 

I tried adding the "norestore" command to the "boot" command in Grub's menu.lst file; same thing. Am using Windows right now to send this. Any & all suggestion will be greatly appreciated...

Thanks a ton.

---

