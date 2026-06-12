---
title: "grub reinstall problem"
date: 2010-11-17
forum: General Help
---

### Post by tibbar_eht on 2010-11-17
I had to reload my XP partition and my grub menu disappeared.  I followed direction from this web page 

[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202)

I followed Method 1. After I rebooted I got a command prompt with a notice stating Minimal BASH-like line editing is suppoerted.  When I input the final command of sudo update-grub I get the unknown command error.  I cannot get to either XP or Ubuntu is there anything I can do short of reloading my ubuntu?

---

### Post by lmarmisa on 2010-11-17
I have used the method #3 several times and it worked fine for me.

If you are unable to restore the GRUB loader, this is an alternative method to restore the XP loader:

```

sudo dd if=/usr/lib/syslinux/mbr.bin of=/dev/sda

```

Maybe it could be a temporary solution if you have priblems with GRUB.

---

### Post by tibbar_eht on 2010-11-17
lmarmisa, thanks at least I have XP back for now.  I guess I will try Method 3 to see if that will work.

---

