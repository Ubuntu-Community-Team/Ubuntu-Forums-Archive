---
title: "gnome-mplayer-1.0.4 help please!!!"
date: 2011-09-02
forum: General Help
---

### Post by rostom_zer on 2011-09-02
hello every one

I wanna compile the package gnome-mplayer-1.0.4 to install it

but terminal gave me these missing packages

No package 'gtk+-2.0' found
No package 'glib-2.0' found
No package 'gthread-2.0' found

please help

thanX in advance

cheers...

---

### Post by spiky001 on 2011-09-02
Mplayer is in the software centre, Is there a reason you dont use that

---

### Post by rostom_zer on 2011-09-02
i installed the mplayer

and i wanna install the " gnome-mplayer " which is the GUI interface of the mplayer

---

### Post by spiky001 on 2011-09-02
It is in software centre type gnome mplayer in search box

---

### Post by rostom_zer on 2011-09-02
It's an old version (0.9.9.2-1) and the new version is 1.0.4

i just wanna ask about the mising packages how to get them because they does not exists in the package manager

how to get them ?

---

### Post by mc4man on 2011-09-02
Start with - 
```
sudo apt-get install libgtk2.0-dev libglib2.0-dev dpkg-dev
```
Then fill in any other missing if needed

---

