---
title: "Battery Alert"
date: 2010-02-18
forum: General Help
---

### Post by RedSingularity on 2010-02-18
Is there a way to change the battery alert in ubuntu?  I want it to alert me when the battery discharge gets to, say, 15%.

---

### Post by cariboo on 2010-02-18
Press Alt-F2 and type:

```
gconf-editor
```

then go to apps->gnome-power-manager->thresholds. You can set:

[list]
[*] percentage_action
[*] percentage_critical
[*] percentage_iow
[/list]

---

### Post by RedSingularity on 2010-02-19
Great!  Thanks cariboo.

---

