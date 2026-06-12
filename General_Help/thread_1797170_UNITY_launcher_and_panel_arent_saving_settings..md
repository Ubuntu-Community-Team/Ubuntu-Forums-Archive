---
title: "UNITY launcher and panel arent saving settings."
date: 2011-07-04
forum: General Help
---

### Post by tjeremiah on 2011-07-04
When I go to change the clock setting, to put it back to a 24hr option, it doesnt work and nothing changes. When I load up dconf-editor to apply more apps. to the panel I cant, because dconf-editor also doesnt allow me to change anything.

Whenever I put an app on the UNITY launcher, it allows me to add and remove, but once I logout than back in, my launcher settings go right back to the default launcher (home folder, firefox, followed by libre office apps)

What gives ?

---

### Post by yanychar on 2011-07-31
Same here. Any luck fixing the issue?

---

### Post by yanychar on 2011-07-31
It seems unity dependencies are not correct.

This fixed the issue for me:
```
$ sudo apt-get install ubiquity-frontend-gtk ubuntuone-control-panel-gtk
$ unity --reset
```

Then wait until no new text and press Ctrl-C. Then reboot or restart gdm.

---

