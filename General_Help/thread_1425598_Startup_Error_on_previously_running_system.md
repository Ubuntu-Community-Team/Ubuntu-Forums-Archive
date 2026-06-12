---
title: "Startup Error on previously running system"
date: 2010-03-09
forum: General Help
---

### Post by MichChampagnie on 2010-03-09
Good Morning,

I upgraded from Hardy to Karmic. All was well for a week. Last night my system wouldn't boot. I tried the previous versions on the boot menu but none of them got me any further. I have no GUI.

I'm a new user so my knowledge isn't very deep but I'm willing to try and fix this as opposed to wiping and starting over.

The error is

USplash: Setting mode 1600x1200 failed
USplash: Using mode 1280x1024
/sbin/apparmor_parser: Unable to replace "/user/share/gdm/guest_session/xsession". Profile version not supported by apparmor module. General error mounting file systems.

I'd appreciate any help or pointers in the right direction. I haven't been able to make heads or tails out of what I've found online.

Thanks.

---

### Post by MichChampagnie on 2010-03-09
I've solved my problem. Thank you

---

### Post by saejin on 2010-03-10
> **MichChampagnie said:**
> I've solved my problem. Thank you
I have the same problem.... what was the solution?

---

### Post by MichChampagnie on 2010-03-10
I rebooted and selected Recovery Mode. From the Recovery Menu, I selected repair broken packages. I saw it reload the drivers for my Radeon Card. (It required the install disk) I also repaired the Grub bootloader.

After it rebooted all was well. Hope it helps.

---

