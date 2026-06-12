---
title: "Karmic Desktop - How to disable GUI at login"
date: 2010-01-24
forum: General Help
---

### Post by meerola on 2010-01-24
Hi,

I'm running Ubuntu Desktop as a media server without a monitor. I upgraded from 9.04 to 9.10 yesterday and the following problem occurred.

The system was configured to boot directly to text-only mode. After the upgrade it started booting to the graphical login screen and I haven't been able to change it back to text-only. I've been googling for a day now, without luck.

I'm still using Grub (ie. not Grub2) because the upgrade failed.

I have used sysv-rc-conf to edit runlevel 3 to not include gdm or kdm. I edited /boot/grub/menu.lst and added 3 to the end of the kernel line (after quiet).

None of this has helped. Any ideas?

Thanks in advance!

---

### Post by Saiko Berry on 2010-01-24
Um.. You can try going into the gnome desktop environment, going to login settings, setting it to skip the login screen, then log out, log into an xterm session and reboot. It should boot directly into xterm each time.

Or.. you can just boot to the login screen then hit alt+ctrl+f1 to jump to tty1.

---

### Post by meerola on 2010-01-24
> **Saiko Berry said:**
> Um.. You can try going into the gnome desktop environment, going to login settings, setting it to skip the login screen, then log out, log into an xterm session and reboot. It should boot directly into xterm each time.

Thanks for the quick reply. However, I wouldn't like the system to login automatically. What I would like is to boot to an xterm login screen. That's how it worked in 9.04.

---

