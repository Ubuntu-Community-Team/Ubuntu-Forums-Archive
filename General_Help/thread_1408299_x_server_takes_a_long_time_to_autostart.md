---
title: "x server takes a long time to autostart"
date: 2010-02-16
forum: General Help
---

### Post by phasmatis on 2010-02-16
Hello, I'm running Ubuntu 9.10 (64-bit). When it boots up, it boots to a text-based login prompt (on tty7). I can log in and do startx manually, but I don't because some things don't work correctly (like wifi). If, however, I wait for a few minutes, the x server starts on tty9 automatically. What could be causing this long delay? What kind of other information should I lok for?

---

### Post by aeiah on 2010-02-16
well it seems something's obviously hanging between booting and X being loaded up. perhaps its X's fault, but perhaps its some unrelated driver module (wifi?) getting stuck 

check dmesg, /var/log/messages and any xorg logs that are in /var/log/messages, eg:

```

dmesg
less /var/log/messages
less /var/log/Xorg.0.log
less /var/log/Xorg.1.log
less /var/log/Xorg.2.log


```

---

### Post by phasmatis on 2010-02-16
Well, there's a few things that are taking a long time. "clocksource tsc unstable" and "freeing invalid memtype". The first one should be easy to fix (using a different clocksource), but I can't find the grub boot menu file location! When I edit any of the usual places, like /boot/grub/menu.lst or /etc/default/grub, none of the changes took effect (as a simple test I changed the names of the boot options, but they didn't change!). Oh well, if I solve it I'll post again.

---

