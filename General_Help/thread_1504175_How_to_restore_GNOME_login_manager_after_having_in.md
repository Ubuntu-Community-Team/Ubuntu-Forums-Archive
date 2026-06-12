---
title: "How to restore GNOME login manager after having installed KDE/Xfce"
date: 2010-06-07
forum: General Help
---

### Post by Calixte on 2010-06-07
I've been testing several DE's and WM's on my normal Ubuntu OS recently. The last one I've installed was KDE. During the installation, the system asked me if I wanted to use the KDE login manager or the GNOME one. I answered KDE. Unfortunately, the new KDE login manager doesn't provide me with the option to change DE's, which makes it impossible for me to login with anything else than GNOME.
could you please tell me how I can switch back to the gnome login manager, or, alternatively, how I can have more options appear on KDE's
thanks,
-Calixte

---

### Post by SlidingHorn on 2010-06-07
I believe this should work for you: [http://ubuntuforums.org/showthread.php?t=376374](http://ubuntuforums.org/showthread.php?t=376374)

---

### Post by angry_johnnie on 2010-06-07
```
sudo dpkg-reconfigure gdm
```

---

### Post by Calixte on 2010-06-07
works. Thanks a lot guys!

---

