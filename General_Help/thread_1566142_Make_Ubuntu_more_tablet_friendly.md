---
title: "Make Ubuntu more tablet friendly?"
date: 2010-09-02
forum: General Help
---

### Post by demonic_bunny on 2010-09-02
Hey, I just purchased a Motion Computing LS800 off of eBay to use as a digital sketchbook. It didn't come with an OS loaded, so I decided to install Ubuntu. So far I'm doing pretty well with it, but was wondering if there were any settings / applications that I could use to make the OS a bit more friendly towards devices without a physical keyboard. Right now I've enabled onboard, but it isn't the most elegant solution, as there's no easy way to hide / show it, and I haven't found a way to bring it up when waking the device from sleep mode, or when the OS prompts for an administrator password. 

Also, is there a way to assign functions to hardware buttons? This thing has a ton of them, and they're kinda just sitting there. Id like to make use of em.

Thanks a lot guys.

---

### Post by zaphod777 on 2010-09-02
> **demonic_bunny said:**
> Hey, I just purchased a Motion Computing LS800 off of eBay to use as a digital sketchbook. It didn't come with an OS loaded, so I decided to install Ubuntu. So far I'm doing pretty well with it, but was wondering if there were any settings / applications that I could use to make the OS a bit more friendly towards devices without a physical keyboard. Right now I've enabled onboard, but it isn't the most elegant solution, as there's no easy way to hide / show it, and I haven't found a way to bring it up when waking the device from sleep mode, or when the OS prompts for an administrator password. 

Also, is there a way to assign functions to hardware buttons? This thing has a ton of them, and they're kinda just sitting there. Id like to make use of em.

Thanks a lot guys.

the latest 10.10 alpha is supposed to be pretty touch screen friendly.

---

### Post by h38thsc0tt on 2011-01-24
I have a LE1600.  I use a program called easystroke to call up onboard.  I've also have tried to enable the hardware buttons.  From windows i discovered the the buttons are on acpi module named MCO0101.  I am in the process of learning how to write a kernel module for this.  If there is any who knows how do do this your help would be appreciated.

---

### Post by Favux on 2011-01-24
Hi h38thsc0tt,

You might want to look at the thinkpad_acpi.c (in the kernel drivers/platform/x86/thinkpad_acpi.c).  I'm thinking the hotkeys.  There are others, they'd be at /sys/devices/platform/ or the same place in the kernel.

---

