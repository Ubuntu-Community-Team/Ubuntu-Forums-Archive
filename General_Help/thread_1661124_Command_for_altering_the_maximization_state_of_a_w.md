---
title: "Command for altering the maximization state of a window"
date: 2011-01-06
forum: General Help
---

### Post by drpunkerz on 2011-01-06
Is there a command I can implement into a script that I am working on to change the maximization state of a window (maximize/restore)? I know there is a keyboard shortcut (Alt + F10), and I'm not interested in doing that. Any input is appreciated. Thanks!

---

### Post by aeiah on 2011-01-06
maybe wmctrl could help

---

### Post by drpunkerz on 2011-01-06
thanks for the lead. Exactly what I was looking for!

Just incase anyone is interested, you'll need to download wmctrl first:
```
sudo apt-get install wmctrl
```

And use this to remove the maximization state of the currently active window:
```
wmctrl -r :ACTIVE: -b remove,maximized_vert,maximized_horz
```

---

