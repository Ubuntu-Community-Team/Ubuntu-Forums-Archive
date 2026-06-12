---
title: "I lost my pulse volume control"
date: 2009-09-17
forum: General Help
---

### Post by ithinkitschad on 2009-09-17
This is probably a pretty dumb question, but I had installed "gnome-volume-control-pulse" and later accidentally removed it from the panel. And now I don't know how to get it back. I don't see it listed when I click "Add to Panel..." and my only other idea was to uninstall it and reinstall it. Does anyone know how to get it back?

Thanks,
      Chad

---

### Post by ithinkitschad on 2009-09-17
Any ideas?

---

### Post by P4man on 2009-09-17
Try this in a terminal:
```
gnome-volume-control-applet
```

Put it in your session to have it start each login. Its there by default, but I guess you removed it there?

---

### Post by ithinkitschad on 2009-09-17
Thank you for the reply. It seems to be running, just not showing the icon. Heres the output:
chunks@bob:~$ gnome-volume-control-applet
** (gnome-volume-control-applet:11478): DEBUG: Disabling debugging

** (gnome-volume-control-applet:11478): WARNING **: Applet is already running, exiting

Where should I go from here? Thanks again P4man.

---

### Post by P4man on 2009-09-17
then i guess you don't have the notification area on your panel. Add that again.

---

### Post by ithinkitschad on 2009-09-17
> **P4man said:**
> then i guess you don't have the notification area on your panel. Add that again.

No I do, everything else in my system tray is showing up.

---

### Post by Skip Da Shu on 2010-08-01
Yea, I thought so too... add "notification-area" just to be sure, if it's dup you can just delete it.

---

