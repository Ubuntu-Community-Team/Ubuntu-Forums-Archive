---
title: "Need help with CCSM"
date: 2010-02-02
forum: General Help
---

### Post by nav16een on 2010-02-02
Guys.. i just now installed compizconfig in my system. I was just testing all the visuals. I enabled reflection. all of a sudden my system got hung. I had to force shutdown my system. I rebooted again and could reach only till my login screen. After i enter my password, the mouse appears and stops. my desktop also doesn't come. everything is hung again. Then i went into the recovery mode. i removed compizconig. The problem still persistes.. Please help me guys.. URGENT...

---

### Post by nav16een on 2010-02-02
guys.. i logged in using guest user. I got the desktop. now i created an administrator. now i logged in using that user to open the application manager. how should i remove all the settings of that user???

---

### Post by Leppie on 2010-02-02
if it's only compiz giving you troubles, you can try renaming the .config and the .compiz folders from the other account:
```
sudo mv /home/<username>/.compiz /home/<username>/.compiz.old
sudo mv /home/<username>/.config /home/<username>/.config.old
```
this should reset *all* gnome and compiz settings (and possibly other settings as well).

---

### Post by nav16een on 2010-02-02
Thanks Leppie.. actually i did a long procedure.. i'd like to share it. I removed compiz plugins from the package manager and then tried logging into my old acc. It went inside but it was very slow. Then i installed compizconfig settings manager alone. Diabled the reflection option. then installed the compiz plugin again.. it restored very quickly and now my system is good as new.. I was totally freeked out in the begining. At last i restored my system.. It took me 3hrs to do this.

---

### Post by Leppie on 2010-02-02
well, at least it's working again. that's important ;)

---

