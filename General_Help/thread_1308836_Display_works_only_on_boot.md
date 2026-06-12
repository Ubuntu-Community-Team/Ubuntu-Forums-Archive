---
title: "Display works only on boot?"
date: 2009-10-31
forum: General Help
---

### Post by Cthulhu_Dreams on 2009-10-31
When I turn on my computer the display works fine.  It isn't until it tries to load the Ubuntu login screen that it goes black...and not the "on" black but rather the off black.  The screen is on (the light shows this) and it plays that drum thing.  Can anyone help me out here?

---

### Post by klemes on 2009-10-31
You can try to boot into repair mode (no Xorg-it's the choice just underneath normal boot in the grub menu)
and choose to drop you into a root shell and then type : 

 ```
dpkg-reconfigure -p high xserver-xorg
```

and then reboot normally  and see if it's been fixed.

---

### Post by Cthulhu_Dreams on 2009-10-31
Nope

---

### Post by klemes on 2009-11-01
Then boot into repair mode and try as root :

```
Xorg -configure
```

followed by :

```
Xorg -config /root/xorg.conf.new
```

just to test if the new xorg.conf if it works.

If it works then give as root:

```
cp /root/xorg.conf.new /etc/X11/xorg.conf
```

and reboot.
Hopefully if everything's done correctly you will boot into gui mode.

---

### Post by Cthulhu_Dreams on 2009-11-01
Still nothing. :/

---

### Post by Cthulhu_Dreams on 2009-11-02
bump

---

### Post by Cthulhu_Dreams on 2009-11-03
Bump....

---

### Post by Cthulhu_Dreams on 2009-11-05
Bump

---

