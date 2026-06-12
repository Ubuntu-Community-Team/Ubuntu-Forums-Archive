---
title: "Network manager broke?"
date: 2009-06-27
forum: General Help
---

### Post by Jestersage on 2009-06-27
I think it may have been mentioned before, but I found out that, if I use GNOME GUI (network connection under systems) to configure the ethernet interface and click "available to all users", which I click apply, the interface (and connection) disappear.

While I can configure it with ifconfig, it doesn't feel right to have even one part of the the GUI broken. Aside from removing GNOME (leaving me with XFCE, LXDE, and KDE) is there other way to fix the applet?

Thanks!

---

### Post by Jestersage on 2009-06-28
Bump

---

### Post by Jestersage on 2009-06-28
Bump again; if you have no idea what I am talking about, can you please at least let me know, so I can do my best to rephrase the question? Or is everyone have no documentation at all when it comes to GUI?

---

### Post by t4thfavor on 2009-06-29
Its a pretty well known fact that Network Manager is broken in more ways than that. Checkout launchpad for a better look. You can replace it with something else if all you need is basic networking, but for advanced stuff I just remove it and go commandline.

---

### Post by Jestersage on 2009-06-29
> **t4thfavor said:**
> Its a pretty well known fact that Network Manager is broken in more ways than that. Checkout launchpad for a better look. You can replace it with something else if all you need is basic networking, but for advanced stuff I just remove it and go commandline.

Thanks. I am the kind of guy that prefer to not keep something broken, because it seems to show flaws more than anything. Removing it does seems to make it more complete. (It's a server anyway)

---

### Post by t4thfavor on 2009-06-29
Sucks that this is the only answer, seems logical that after this same thing happens countless other times that there would be a bit more effort to fie it.

Some people use it and never have problems, while others have the exact opposite experience.

---

### Post by itsjareds on 2009-06-29
I recommend using Wicd instead, I had to remove Network Manager as well because of some other issues. Wicd works fine and integrates well into your GUI with a system tray.

To install Wicd, open your terminal and type this:
```
sudo apt-get autoremove network-manager
sudo apt-get install wicd
```

This should do it, you'll just have to configure your network after this.

---

### Post by Jestersage on 2009-06-29
Yes, doing it right now. If it doesn't feel broke, I may keep it

---

