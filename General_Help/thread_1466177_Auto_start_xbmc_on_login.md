---
title: "Auto start xbmc on login"
date: 2010-04-30
forum: General Help
---

### Post by DaveHope on 2010-04-30
Hi,

I've bought myself an Acer Revo and have 10.04 running nicely on it. After some basic tweaks I have 1080p content playing flawlessly.

However, I'd like the system to boot directly into xbmc (no gdm etc). Can anyone suggest how this might be achieved?

Under 9.10 I used a minimal install and edited /etc/event.d/tty1 to login a user. .bash_profile was then edited to start xbmc.

Given that event.d is now gone, any suggestions?

---

### Post by DaveHope on 2010-04-30
*Bump*

---

### Post by Aenima99x on 2010-04-30
There's a ton of ways to do it, check out the [XBMC Forums]("http://forum.xbmc.org").
The way I'm currently doing it is by editing ```
/etc/init/tty1.conf
``` and changing ```
exec /sbin/getty 38400 tty1
``` to ```
exec /bin/login -f xbmc </dev/tty1 > /dev/tty1 2>&1
```. However I'm fairly certain you'll need the xbmc-live package installed to do it this way.

---

### Post by DaveHope on 2010-04-30
Thanks for the reply, I'd tried that too (should have mentioned it) but no such luck.

This is presumably because gdm etc is still starting? - How can I prevent that (I've tried using rcconf, but the only option there was x11-common which seems unrelated).

---

