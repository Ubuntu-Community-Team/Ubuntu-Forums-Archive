---
title: "Systray psychosis"
date: 2010-05-03
forum: General Help
---

### Post by QwUo173Hy on 2010-05-03
I'm getting a messed up menu-bar / system-tray. It doesn't happen every boot. I also don't quite know what to file a bug against (indicator applet, notify-osd, gnome-panel?)

I'm getting this on two Lucid machines. Anyone?

---

### Post by dino99 on 2010-05-03
metacity --replace

sudo dpkg --configure -a

---

### Post by QwUo173Hy on 2010-05-04
> **dino99 said:**
> metacity --replace

sudo dpkg --configure -a
```
Window manager warning: Failed to read saved session file /home/jarlath/.config/metacity/sessions/10cc3b9decf3199da412729564865362000000013550000.ms: Failed to open file '/home/jarlath/.config/metacity/sessions/10cc3b9decf3199da412729564865362000000013550000.ms': No such file or directory

```

---

