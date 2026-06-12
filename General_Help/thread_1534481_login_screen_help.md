---
title: "login screen help"
date: 2010-07-19
forum: General Help
---

### Post by owners4life5 on 2010-07-19
well...

i have a kind of...... 'bug' when logging in.

see a few days ago, i followed a how-to (I can.t recall where it is located) on how to change the background of the login screen. i figured it out and followed the directions, but now every time i go to log in, it shows the 'appearance' menu, where you can select the theme, desktop, etc, and it just has become a bit of a pain. i would like to get this problem solved as soon as possible, but no hurry.

any help is greatly appreciated
thanks

---

### Post by sisco311 on 2010-07-19
You have to remove gnome-appearance-properties from the autostarted applications:

```
sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop
```

---

### Post by owners4life5 on 2010-07-19
rebooted. works like a charm. thank you

---

### Post by etdsbastar on 2010-07-19
> **owners4life5 said:**
> rebooted. works like a charm. thank you

Its good to see a charming face. But, I would appreciate if you will make the thread as solved.

---

### Post by owners4life5 on 2010-07-19
well i didn.t have it solved 3 minutes ago...

---

### Post by sisco311 on 2010-07-19
> **owners4life5 said:**
> rebooted. works like a charm. thank you

You're welcome!

---

