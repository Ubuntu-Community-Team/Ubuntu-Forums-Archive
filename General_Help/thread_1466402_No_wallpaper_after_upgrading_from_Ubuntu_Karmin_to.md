---
title: "No wallpaper after upgrading from Ubuntu Karmin to LTS ?!"
date: 2010-04-30
forum: General Help
---

### Post by red33m on 2010-04-30
Hello forum,

I just installed Ubuntu 10.04 LTS and I have a problem. No wallpaper.I can only have a white one and when I try changing it, the white one always come back!

During the upgrade from Ubuntu 9.10 it asked me to delete some packages(during the cleanup) and so I did. They were named lib..something.

Please help!!

Don't know if it has something to do with it but I can't see the slash screen either.(I don't care about that so much)

Thanks in advance

---

### Post by philinux on 2010-04-30
Try this.

```
sudo apt-get install --reinstall ubuntu-desktop
```

Or use synaptic to do it.

---

### Post by red33m on 2010-04-30
didn't work..

other suggestions ?

---

### Post by red33m on 2010-04-30
Come on guys!

Can anybody hear me???!!!!

---

### Post by jamesdcarroll on 2010-06-14
Check gconf/desktop/gnome/background/draw_background.  I had a similar problem on 9.10 and turning that back on fixed it.

---

### Post by red33m on 2010-06-14
> **jamesdcarroll said:**
> Check gconf/desktop/gnome/background/draw_background.  I had a similar problem on 9.10 and turning that back on fixed it.

How do I turn it on?

N00B needs help!

---

### Post by Gryphen on 2010-06-18
> **red33m said:**
> How do I turn it on?

N00B needs help!
alt+f2 gconf-editor

I have (almost) the same problem gconf/desktop/gnome/background/draw_background was already true. :(

---

### Post by Gryphen on 2010-06-20
It will probably be fixed in a upgrade for now I'm using KDE.

---

### Post by nick_goodfate on 2010-10-09
Same problem here. It's like something covers wallpaper. I do killall nautilus, and wallpaper shows up for a second! then something restarts and covers it... I also have this problem since the last update...

---

