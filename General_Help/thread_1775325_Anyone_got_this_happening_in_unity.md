---
title: "Anyone got this happening in unity"
date: 2011-06-04
forum: General Help
---

### Post by notoriousdbp on 2011-06-04
Basically, on my daughters eeepc 701SD when unity loads it looks normal to start with then switches to what looks like a default gnome appearance as per the screenshot attached.  You can tell it's going to happen because the workspace switcher has a purple background instead of a grey one.

Has anyone else had the problem and is there a fix?

---

### Post by Larkspur on 2011-06-04
> **notoriousdbp said:**
> Basically, on my daughters eeepc 701SD when unity loads it looks normal to start with then switches to what looks like a default gnome appearance as per the screenshot attached.  You can tell it's going to happen because the workspace switcher has a purple background instead of a grey one.

Has anyone else had the problem and is there a fix?

Basically, the gnome-settings-daemon is starting too soon.  Try this in the terminal:

```
killall gnome-settings-daemon
```

Then, after that:

```
gnome-settings-daemon
```

This shouldn't happen very often, but if your daughter keeps having problems, try the procedure outlined in [this]("http://www.webupd8.org/2011/06/fix-ubuntu-linux-mint-theme-changing-to.html") article, which also explains why it can happen.

---

### Post by notoriousdbp on 2011-06-04
Thanks, worked a treat :)

---

