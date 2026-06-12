---
title: "How do I recover Windows booting capability?"
date: 2011-03-01
forum: General Help
---

### Post by rva1945 on 2011-03-01
I have two partitions Windows XP (which was already installed before Ubuntu) and Ubuntu 9.1 (which I installed later).

Now the XP doesn't boot anymore (sorry but I need it sometimes), the Windows screen with the progress bar appears and then it reboots after a couple of secs.

I can access to the XP partition from Ububtu.

Of course I don't want to damage Ubuntu during the XP recovery action.

Thanks

---

### Post by Krytarik on 2011-03-02
It seems like your Windows itself is damaged, if it were Ubuntu's boot loader it wouldn't even begin to boot.

You could try to replace Grub (Ubuntu's boot loader) with Windows' boot loader to rule out the last bit:
[http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/](http://helpdeskgeek.com/how-to/fix-mbr-xp-vista/)

If you need to eventually re-install Windows, Grub would be replaced anyways.

Restoring Grub is pretty simple, follow this guide, use a LiveCD/InstallCD therefore:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")

---

