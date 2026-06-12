---
title: "uptime problems"
date: 2010-04-08
forum: General Help
---

### Post by Caesum on 2010-04-08
Hi,

I've got a few processes running that will take a long time to complete so I don't really want to reboot but.......the computer hasn't been rebooted for 43 days but in the meantime all icons in Gnome have eventually just become the same little square box, and for some reason no matter what CD i put in nothing seems to happen, no files are listed, no cd seems to be mounted or files listed.

So, is there some way to refresh the icons and restart the cd driver?

Thanks

---

### Post by The Real Dave on 2010-04-08
Can you log out and log back in? A similar thing happens to me if I run something that hogs resources for a long time, the Nautilus desktop disappears, and Gnome-Panel stops working. I usually just restart both, but a log out solves the problem also, for me at least.

---

### Post by Caesum on 2010-04-08
Hmm, not sure I can do that, I have processes started from within Gnome, will they be killed? If not, how do I 'reconnect' to them?

---

### Post by srs5694 on 2010-04-08
Try this:

```

echo "exec gnome-session" > ~/.xinitrc
startx -- :1 vt8

```

This should start another X session on VT8 (press Ctrl+Alt+F8 to get to it, then press Ctrl+Alt+F7 to get back to your current session). If you need to do this again, omit the echo command; just go straight to the startx command. (The echo command creates a basic X configuration file that starts GNOME. This file will still exist when you run startx again.)

---

