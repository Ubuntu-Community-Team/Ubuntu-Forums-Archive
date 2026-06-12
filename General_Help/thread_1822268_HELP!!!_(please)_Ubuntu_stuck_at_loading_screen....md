---
title: "HELP!!! (please) Ubuntu stuck at loading screen..."
date: 2011-08-10
forum: General Help
---

### Post by Keypel on 2011-08-10
I commented out the contents of 

/etc/X11/default-display-manager

I was trying to start Ubuntu without a GUI so I could improve my Linux knowledge.

When I rebooted I get stuck on the Ubuntu screen with the four loading dots.

When I hit Esc I get this

```
 2 logical volumes(s) in volume group "PC-01" NOW ACTIVE
fsck from util-linux-ng 2.17.2
fsck from util-linux-ng 2.17.2
/dev/mapper/PC--01-root: clean, blah/blah files, blah/blah blocks
/dev/sda1: clean, 219/124496 files, 63828/248832 blocks
* Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disbale: usr.bin.firefox

*Settnig sensors limits
*Starting virtual private network daemon(s)...
speech-dispatcher disabbled; edit /etc/default/speech-dispatcher
*Starting VirtualBox kernel modules
GStarting the Winbind daemon winbind
*PulseAudio configured for per-user sessions
naned disabled; edit /etc/default/saned
*Enabling additional executable binary formats binfmt-support
*Checking battery state...
```

There is a flashing underscore but I cannot type anything.

---

### Post by SeijiSensei on 2011-08-10
If you want to run from the command line, choose the "recovery" option in the GRUB menu at start up.  This will give you a nice text-only login.

---

### Post by couling on 2011-08-10
I've had the same thing start happening with my pendrive install for one of my machines.  I still havn't managed to fix it yet, but it seems to work fine in my laptop.

---

### Post by Keypel on 2011-08-10
I noticed if I hit Esc before it gets to the part where it normally gets stuck, then it won't get stuck.

---

