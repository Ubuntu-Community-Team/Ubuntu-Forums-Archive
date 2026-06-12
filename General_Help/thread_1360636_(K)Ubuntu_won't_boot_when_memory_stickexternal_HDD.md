---
title: "(K)Ubuntu won't boot when memory stick/external HDD is connected"
date: 2009-12-21
forum: General Help
---

### Post by TWO on 2009-12-21
Hello all.

I'm currently running Kubuntu Karmic Koala with all the latest updates applied as of 21st December 2009 on a Dell Inspiron 1300 laptop- they don't make these any more.

Anyway, I've noticed that Kubuntu will not boot if I have either my memory stick or external HDD connected to it. 

In my experience, having the external HDD connected leaves a black screen with a flashing cursor, and it doesn't progress from this page. This is prior to when the Kubuntu boot splash should appear. I should mention here that the HDD is formatted to NTFS, if this has any bearing.

As for the memory stick, when I left this connected when rebooting, I was greeted with a "Operating System Not Found" message, to which I was obviously quite surprised. Removing the memory stick and restarting proved otherwise. 

It might be worth mentioning that I installed Kubuntu via the USB method, and I know that once upon a time, this method used to cause issues with any subsequent USB memory devices that would be connected to the system, this being something to do with an entry for the installation device being written into etc/fstab, though in this case, I don't think there is any entry. 

I'm just wandering if this is a widespread problem, if it has been reported and if there are any solutions? 

Thanks in advance

TWO

---

### Post by DeMus on 2009-12-21
> **TWO said:**
> Hello all.

I'm currently running Kubuntu Karmic Koala with all the latest updates applied as of 21st December 2009 on a Dell Inspiron 1300 laptop- they don't make these any more.

Anyway, I've noticed that Kubuntu will not boot if I have either my memory stick or external HDD connected to it. 

In my experience, having the external HDD connected leaves a black screen with a flashing cursor, and it doesn't progress from this page. This is prior to when the Kubuntu boot splash should appear. I should mention here that the HDD is formatted to NTFS, if this has any bearing.

As for the memory stick, when I left this connected when rebooting, I was greeted with a "Operating System Not Found" message, to which I was obviously quite surprised. Removing the memory stick and restarting proved otherwise. 

It might be worth mentioning that I installed Kubuntu via the USB method, and I know that once upon a time, this method used to cause issues with any subsequent USB memory devices that would be connected to the system, this being something to do with an entry for the installation device being written into etc/fstab, though in this case, I don't think there is any entry. 

I'm just wandering if this is a widespread problem, if it has been reported and if there are any solutions? 

Thanks in advance

TWO

When the external drives/sticks are connected the computer tries to boot from them. When it can not because there is no OS there it will stop. Quite normal.

---

### Post by Leppie on 2009-12-21
you can change the boot order in your laptop's bios and possibly disable booting off usb devices. if you never use bootable usb drives this may be a good choice, but since you did a usb install i'd say it's better to remove usb drives when shutting down unless you want to use them as boot device on reboot.

---

### Post by TWO on 2009-12-21
> **Leppie said:**
> you can change the boot order in your laptop's bios and possibly disable booting off usb devices. if you never use bootable usb drives this may be a good choice, but since you did a usb install i'd say it's better to remove usb drives when shutting down unless you want to use them as boot device on reboot.

Aha! This would be it! I had completely overlooked the BIOS settings! I presumed it was something to do with Kubuntu itself. 

Gosh I feel a little silly for forgetting about that! :redface: My mind is turning rusty!

Thanks for this though Leppie, I've simply switched the boot order around in the settings and no longer have the issue!

---

### Post by Leppie on 2009-12-21
> **TWO said:**
> Aha! This would be it! I had completely overlooked the BIOS settings! I presumed it was something to do with Kubuntu itself. 

Gosh I feel a little silly for forgetting about that! :redface: My mind is turning rusty!

Thanks for this though Leppie, I've simply switched the boot order around in the settings and no longer have the issue!

glad it worked out.
you may want to switch the settings back when you need to do another usb install though ;)

---

