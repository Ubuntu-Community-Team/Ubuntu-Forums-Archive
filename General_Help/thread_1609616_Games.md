---
title: "Games"
date: 2010-10-30
forum: General Help
---

### Post by U_buntu on 2010-10-30
I downloaded a few games like Unreal Tournament GOTY, when I try to install them, it wants me to mount the disc. How do I do this?

---

### Post by zvacet on 2010-10-31
If games are iso.files then type in terminal

```
sudo mkdir -p /media/cdrom

```

and if you downloaded games in your desktop 

```
sudo mount -o loop ~/Desktop/game_name /media/cdrom
```

---

