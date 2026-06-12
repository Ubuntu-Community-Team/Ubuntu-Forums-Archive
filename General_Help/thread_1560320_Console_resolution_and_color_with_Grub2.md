---
title: "Console resolution and color with Grub2"
date: 2010-08-24
forum: General Help
---

### Post by JKyleOKC on 2010-08-24
I've got a small problem that's nagging me, and need ideas from anyone. I prefer more lines on the screen when using the virtual terminals (ctrl-alt-F1 and so on) than I get with the default settings.

After much research, I found that as of Grub 1.98, which comes with 10.04.1, a line in /etc/default/grub to set GRUB_GFXPAYLOAD_LINUX can set the resolution for all of the virtual terminals.

However, if I set it as 1024x768x32, the terminals come out green on black rather than my preferred white on black. That's usable but hard on my aging eyes. If I set it as 1024x768x8, they are light gray on black and very difficult to read.

Apparently something somewhere in the boot process between the time that grub2 sets the payload, and the time that the boot completes, changes the foreground color. I'm looking for the command (or script) that can do so globally, so that I can include it in /etc/rc.local and set the console foreground color the way I want it. Anybody know what that might be, or even where to start looking for it?

Fiddling with xorg.conf won't do it, since the VTs don't use the X server at all...

---

