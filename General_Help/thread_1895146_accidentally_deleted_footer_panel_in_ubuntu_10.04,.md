---
title: "accidentally deleted footer panel in ubuntu 10.04, how bring it back"
date: 2011-12-14
forum: General Help
---

### Post by lse123 on 2011-12-14
PCMCIA Xircom cem56-100 56K/100ETHERNET CARD, drivers can installed automatically, how?

I accidentally deleted footer panel in ubuntu 10.04, how bring it back?

---

### Post by BC59 on 2011-12-14
Press CTRL+ALT+T to open a terminal and run:

```
killall gnome-panel
```

---

### Post by BC59 on 2011-12-14
If that fails try:

```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

---

### Post by lechien73 on 2011-12-14
> **lse123 said:**
> I accidentally deleted footer panel in ubuntu 10.04, how bring it back?

This procedure will get back your panel with default settings. Open a terminal window and type:

```
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel
```

---

### Post by lse123 on 2011-12-22
> **BC59 said:**
> If that fails try:

```
gconftool-2 --recursive-unset /apps/panel
killall gnome-panel
```

killall isn't about delete? I want retrieve bottom panel that i deleted by error...10.04 ubuntu...

---

### Post by plucky on 2011-12-22
> **lse123 said:**
> killall isn't about delete? I want retrieve bottom panel that i deleted by error...10.04 ubuntu...

No,it will stop the process which will then auto restart and hopefully you will have both panels back.

Good luck

---

