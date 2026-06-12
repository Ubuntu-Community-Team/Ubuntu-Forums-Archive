---
title: "Need help customizing a window sizing hotkey"
date: 2010-05-05
forum: General Help
---

### Post by pizzystrizzy on 2010-05-05
Hi all, linux newbie here --   there is a feature in windows 7 that I would love to make work here.   I'm sure there is some way to do it, given how customizable linux is,  but I have no idea how.

In windows 7, if you hit the Windows key +  the left arrow, it will automatically resize the window you are looking  at to fill half the screen, on the left side.  Likewise if you push the  right arrow, for the right side,  Windows+up arrow maximizes, and  windows + down arrow minimizes.  

Does anyone have an idea of how  I can configure ubuntu to do the same thing?

---

### Post by pizzystrizzy on 2010-05-05
bump.

---

### Post by VCoolio on 2010-05-05
Use wmctrl and find out what command you need to fit your monitor resolution. To move a window to the left half of the screen, I use this for 1024x768 with a dock to reckon with (hence 691 instead of 768 ):
```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,508,691
```

The same, for right half and top half:
```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,511,0,508,691
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz;wmctrl -r :ACTIVE: -e 0,0,0,1018,290"
```

Edit: bumping after 4 hours is considered pretty soon; better be a bit more patient.

---

