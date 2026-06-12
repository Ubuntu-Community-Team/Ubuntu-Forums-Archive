---
title: "Gnome-Panel problem."
date: 2009-11-01
forum: General Help
---

### Post by Oriyama on 2009-11-01
I've searched all over the internet and tried to fix the problem myself, but nothing seems to work.

After downloading Avant Window Navigator, I decided to remove all the applets from my gnome-panel and hide it. Problem was that after hiding it, the panel refused to reappear. I went into gconf-editor and managed to restore the size, but now the panel is a solid white / transparent colour and when right clicked, only displays 'Help' and 'About Panels'. I'm not quite sure what I had done that my panel would become like this. I am using 9.10, any help would be great.

---

### Post by Oriyama on 2009-11-01
I've tried uninstalling Gnome-Panel , but it still returns to its useless state when reinstalled.

---

### Post by emigrant on 2009-11-01
log off.
and on your login screen at the bottom left corner,
select a different session.
see whether that works.

---

### Post by Oriyama on 2009-11-01
Uh no, it managed to screw it up even more. I tried Failsafe GNOME and it kinda made it worse. Compiz crashes when I start up now, which also crashes AWN. Now I have no menus and I'm stuck in a rut.

---

### Post by Oriyama on 2009-11-01
Okay, I logged out and relogged in with regular GNOME. Back to the first problem.

---

### Post by Oriyama on 2009-11-01
I found out how to make the panel look like anything, but when right clicked only Help and About Panel shows up still :S Help Please

---

### Post by DeMus on 2009-11-01
> **Oriyama said:**
> I found out how to make the panel look like anything, but when right clicked only Help and About Panel shows up still :S Help Please

First disable compiz since it is known to be a major pain in the butt.
Set your effects to none. Reboot and see what happens then.

---

### Post by Oriyama on 2009-11-01
Hm, no effect , except that AWN didn't load up and I had to fix that. The panel still doesn't work .

---

### Post by DeMus on 2009-11-01
> **Oriyama said:**
> Hm, no effect , except that AWN didn't load up and I had to fix that. The panel still doesn't work .

Can it bed you also have matecity running as well? AWN and metacity are two windows managers, but you only need one.

---

### Post by Oriyama on 2009-11-01
Solved the problem following
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Still don't know what the problem in the first place was, but it's solved now. Thanks anyways.

---

### Post by DeMus on 2009-11-01
> **Oriyama said:**
> Solved the problem following
[http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html](http://www.watchingthenet.com/restore-panels-in-ubuntu-back-to-their-default-settings.html)

Still don't know what the problem in the first place was, but it's solved now. Thanks anyways.

It looks to me they are completely shutting down the panels and also remove information about them in your home folder.
Well happy it works again as it should. Have fun.

---

