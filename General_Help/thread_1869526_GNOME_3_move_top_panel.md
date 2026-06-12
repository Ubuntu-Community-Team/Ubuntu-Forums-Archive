---
title: "GNOME 3 move top panel"
date: 2011-10-25
forum: General Help
---

### Post by iconoclast hero on 2011-10-25
I'm using a laptop with an external monitor.  I would like to make the "primary monitor" the external monitor and move the top panel to that one.  I can't  figure out how move the top panel from one monitor to the other.  Additionally, when I hit the windows key, everything appears on the laptop monitor and not on the external monitor.  

Is there some way to change this?

---

### Post by SadisticCheeto on 2011-10-25
xrandr should help with that. You can run xrandr without any arguments to get the list of displays.
```
xrandr --output <display> --primary
```

---

### Post by iconoclast hero on 2011-10-26
Thanks!

---

### Post by iconoclast hero on 2012-03-07
And it still works in the fall back gnome session of 12.04 LTS B1.  I hate Unity.

---

