---
title: "a problem with X-server"
date: 2006-04-27
forum: General Help
---

### Post by master.durin on 2006-04-27
I had a geforce2-mx200 video card. Then I replaced it by ATI RADEOn 9250. since that, UBUNTU can't be loaded and I have a title "X-server has a problem to load, please update your settings"

Anybody may explain me how to do that?

Thanks a lot.

---

### Post by olsonar on 2006-04-27
I think this is just because xorg.conf wasn't updated with your card. If you can get to a command prompt, just enter this to update it:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Hope this helps!

---

### Post by master.durin on 2006-04-27
[QUOTE=olsonar]I think this is just because xorg.conf wasn't updated with your card. If you can get to a command prompt, just enter this to update it:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Hope this helps![/QUOTE]


THANKS A LOT!!! IT WORKS! I'M IN LINUX NOW :-)))

---

