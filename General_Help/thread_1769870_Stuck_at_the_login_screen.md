---
title: "Stuck at the login screen"
date: 2011-05-28
forum: General Help
---

### Post by eLancaster on 2011-05-28
Whenever i log in to ubuntu, my cursor doesn't move on the log in screen. I can't choose my account, can't sign in. Why's this happening and is there a way to fix it without reinstalling ubuntu.

P.S. Ubuntu 10.10 (Maverick Meercat)

---

### Post by sanderd17 on 2011-05-28
Can you press CTRL+F1 and see if you can log in?

If you can, try the command 
```

top

```
to see what process is blocking your computer.

---

### Post by eLancaster on 2011-05-28
I just tried that. It didn't work.
It seems I can't do anything on the log-in screen.

---

### Post by prodigy_ on 2011-05-28
Can you boot from a Live CD? If it causes your PC to hang as well, then you likely have a faulty or unsupported device (though "unsupported" is a broad term, it might be just a broken driver in a particular kernel version).

If booting from Live CD works alright, you should try to run Ubuntu in recovery mode (there's an option for that in Grub menu) and look for any relevant error messages in system logs (mainly **/var/log/syslog** and **/var/log/dmesg**). Alternatively you can access your logs from Live CD, you just need to mount the right partition from your installation first.

---

### Post by linuxinstalledfromhdd on 2011-05-28
I would try creating a Live USB stick of Ubuntu 10.10 to install from, instead of using a Disc and see if that makes any difference.

---

### Post by sanderd17 on 2011-05-29
Oh damn, what a mistake from me, it should be CTRL+ALT+F1.

But if that doesn work, try the live CD/USB.

---

