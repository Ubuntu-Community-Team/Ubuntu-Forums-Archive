---
title: "font not appearing in openoffice"
date: 2009-08-05
forum: General Help
---

### Post by ecpepper on 2009-08-05
I installed a font but it isn't showing up in openoffice (writer). It's a truetype font (agaramondpro-regular.ttf) and I installed it simply by placing a copy in a subfolder of /usr/share/fonts/truetype. I then confirmed that the font was properly recognized by running gnome-specimen (the font management program).  It shows up properly in gnome-specimen but when I open openoffice writer, it is not included in the font list. Am I missing a step?

ecpepper 

Ubuntu Jaunty (9.04)
Openoffice 3.0.1

---

### Post by jmszr on 2009-08-05
ecpepper,

If you haven't rebooted,do so. It is necessary for the font to get into open office. If you already have, we'll need to look further,

Also: [https://wiki.ubuntu.com/Fonts](https://wiki.ubuntu.com/Fonts)

---

### Post by gldearman on 2009-08-05
> **ecpepper said:**
> Am I missing a step?

Yep.

Type this

```
sudo fc-cache -f -v
```

You will have to restart any font-using applications (like Open Office) after doing this, if they were open.

---

