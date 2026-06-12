---
title: "button location"
date: 2012-07-18
forum: General Help
---

### Post by oldtraveler on 2012-07-18
I prefer for the minimize and delete buttons to be on the upper right sight of the window. Ubunutu 12.04 seems to want them on the uper left side.  Can I change this?  If so, how?

---

### Post by claracc on 2012-07-19
It seems you can do it through ubuntu  tweak : [http://askubuntu.com/questions/124015/window-controls-moved-to-right-hand-side](http://askubuntu.com/questions/124015/window-controls-moved-to-right-hand-side), from this link:

> I found that the gconf-editor suggestion just reversed the order of the buttons. They remained on the right hand side of the window. To switch buttons to the left hand upper corner, I used System Settings > Ubuntu Tweak > Tweaks > Window. Window Control

---

### Post by Nixarter on 2012-07-19
I just did this moments ago.  Still have the command handy :)

```

gconftool-2 --set "/apps/metacity/general/button_layout" --type string ":minimize,maximize,close"
```From [here]("http://ubuntuforums.org/showthread.php?t=1966370").

It is for metacity in gnome-fallback (not Unity).  So it depends on the DE you are using.

---

### Post by oldtraveler on 2012-07-19
> **claracc said:**
> It seems you can do it through ubuntu  tweak : [http://askubuntu.com/questions/124015/window-controls-moved-to-right-hand-side](http://askubuntu.com/questions/124015/window-controls-moved-to-right-hand-side), from this link:

That worked.  Thank you.

---

