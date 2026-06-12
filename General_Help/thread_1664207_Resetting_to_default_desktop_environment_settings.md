---
title: "Resetting to default desktop environment settings"
date: 2011-01-10
forum: General Help
---

### Post by xtheunknown0 on 2011-01-10
When I sudo apt-get install['ed] kolourpaint, I had to download all the stuff necessary for a KDE environment, I think. When I restarted the machine, everything went from black to light grey. Even NetworkManager went from the three or four curves to the pair of blue monitor computers. How do I restore the desktop environment settings?

Since things changed after a command-line instruction, feel free to post the appropriate command-line instruction.

TIA,
xtheunknown0

---

### Post by Habitual on 2011-01-11
to restore:
logout and Ctl+Alt+F1
login as your normal user and issue...

```

rm -fr .config .gconf

```

then logout of the terminal session and login via GUI (Alt+right arrow until you see the GDM Login)

Your desktop will be default.

Customize away.

---

### Post by xtheunknown0 on 2011-01-11
Thanks for this information.

However, when I restarted the machine (after seeing it with different colours as originally posted), everything went back to normal.

Can you explain this?

TIA,
xtheunknown0

---

