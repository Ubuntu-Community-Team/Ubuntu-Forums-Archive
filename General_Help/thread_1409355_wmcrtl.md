---
title: "wmcrtl"
date: 2010-02-17
forum: General Help
---

### Post by pedrom169 on 2010-02-17
How do install wmctrl. The configure it to split the window's in half across the screen? So one window is half the screen and the other is the rest?

Thanks

---

### Post by darolu on 2010-02-17
```
$ sudo apt-get install wmctrl
```
Or search for "wmctrl" in Synaptic.

You can also try with Compiz (if you use it), browse the Window-manager options in ccsm. If you don't have it install with:
```
$ sudo apt-get install compizconfig-settings-manager
```

---

### Post by VCoolio on 2010-02-17
Here are some wmctrl commands that I've attached to keyboard shortcuts; maybe they can help to figure out what you want. They place windows (in this order): left, right, bottom, top, top left, top right, down left, down right, on a 1024x768 monitor. Read man wmctrl and you should be able to get what you want.

```
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,508,691"
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,511,0,508,691"
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,365,1018,290"
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,1018,290"
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,508,290"
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,511,0,508,290"
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,365,508,290"
"wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,511,365,508,290"

```

---

