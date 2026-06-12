---
title: "GNOME doesn't start?"
date: 2010-01-25
forum: General Help
---

### Post by 14f13 on 2010-01-25
Hello fellas,

I've been messin with Ubuntu for several hours now solving problem using Google and so, but this one I can't overcome and can't find any solution. So I've got Ubuntu 9.10 fresh install, no upgrades and was looking in Emerald Theme Manager to change icons, then suddenly I lost  all windows and saw just cursor and wallpaper, no bars etc. After restart it's same situation. Tried recovery mode to repair packages, but it won't help. Help me in being another happy Ubuntu user ;>. (if you need any more info, let me know how to obtain it, I'm new user ;o )

---

### Post by Leppie on 2010-01-25
in the recovery console, try renaming your .gconf directory:
```
sudo mv /home/<username>/.gconf /home/<username>/.gconf-old
```

then reboot, it should rebuild your gnome settings folder.

---

### Post by 14f13 on 2010-01-26
Thanks mate :D It worked.

---

### Post by Leppie on 2010-01-26
> **14f13 said:**
> Thanks mate :D It worked.
glad it worked, enjoy ubuntu :)

---

