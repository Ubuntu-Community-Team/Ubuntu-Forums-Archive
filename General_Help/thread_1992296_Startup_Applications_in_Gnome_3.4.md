---
title: "Startup Applications in Gnome 3.4"
date: 2012-05-31
forum: General Help
---

### Post by balasankarc on 2012-05-31
Hi all,
In unity, i could select startup applications clicking the gear icon the top-right corner. But now i'he changed to gnome 3.4, where i cannot find such an option.. pls tell me how can i find it.
i want to make cairo dock start automatically on startup

Balasankar C

---

### Post by traditionalist on 2012-05-31
> **balasankarc said:**
> Hi all,
In unity, i could select startup applications clicking the gear icon the top-right corner. But now i'he changed to gnome 3.4, where i cannot find such an option.. pls tell me how can i find it.
i want to make cairo dock start automatically on startup

Balasankar C

The autostart folder is in /etc/xdg 

/etc/xdg/autostart

you can navigate to it and then bookmark it.  Anything you drop into that folder will autostart.

[[IMG]http://img31.imageshack.us/img31/6919/selection001wy.th.png[/IMG]]("http://img31.imageshack.us/i/selection001wy.png/")

---

### Post by imachavel on 2012-05-31
nice

don't forget to gksu nautilus from the terminal line to get sudo permissions to the gui before you drag and drop into that folder. After all, it probably won't allow you without proper permissions

---

### Post by balasankarc on 2012-05-31
> **imachavel said:**
> nice

don't forget to gksu nautilus from the terminal line to get sudo permissions to the gui before you drag and drop into that folder. After all, it probably won't allow you without proper permissions

Thanks Buddy

---

