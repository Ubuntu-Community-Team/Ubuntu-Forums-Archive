---
title: "Slow desktop on Intel 3945-powered laptop"
date: 2009-11-09
forum: General Help
---

### Post by Scooter7 on 2009-11-09
Hi,

I just installed Ubuntu 9.10 fresh on my laptop.   Everything seems to be working well, except that the desktop is graphically slow.   I've had this same problem in Arch Linux.   It seems to be a result of the new X system - the one that doesn't rely on a Xorg.conf file.   I've read about problems with my Intel card, and the fix seems to be editing Xorg.conf, but I don't have one - I'm assuming that's because 9.10 uses the newer X.

I also can't enable Compiz, whereas when I last used Ubuntu, it worked flawlessly.   I think that was with 7.10 or 8.04.

Does anyone know how I could fix this?   One fix might be to generate a Xorg.conf, but I'd rather not mess with that since the new system is supposed to be better.

**Update:** Just tried creating a Xorg.conf with ```
sudo dpkg-reconfigure -phigh xserver-xorg
```   Doesn't do anything, at all.   The output (or lack thereof):

```
vertimyst@shadowgate-lt1:~$ sudo dpkg-reconfigure -phigh xserver-xorg
vertimyst@shadowgate-lt1:~$
```

---

### Post by Scooter7 on 2009-11-09
*bump*

Anyone know of a way I could generate a Xorg.conf?   The usual way isn't working for me.

I think that I've had a similar problem (slow graphical desktop) in Arch Linux, however I could generate a Xorg.conf then to fix it.   If I could get one in Ubuntu that might help.   Something to try, anyway.

---

### Post by Scooter7 on 2010-02-07
Sorry for bumping an old thread.   Just want to say I think I've solved this - I usually disable ACPI through GRUB (acpi=off), so I can get sound support.   But I've just done a fresh install of Kubuntu 9.10, and leaving ACPI enabled kills my sound and other ACPI-related functions (i.e, battery status), but my system runs very fast now.   Also, desktop effects become enabled as well.

Issue solved, though now I'm looking into trying to get sound back via fixing my DSDT.

---

