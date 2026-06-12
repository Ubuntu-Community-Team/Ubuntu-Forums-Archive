---
title: "second display"
date: 2010-02-07
forum: General Help
---

### Post by preit on 2010-02-07
Ok, i have a second monitor attached and is working fine.  but how do i set up the system that when i close my laptop lid (while it is on AC power) to not shut down?  I am sure it is a simple fix, but when i go into power settings "Do Nothing" is not an option.  Any assistance would be greatly appreciated

---

### Post by lostdata on 2010-07-18
Found it try this

```
gconftool-2 --type string --set /apps/gnome-power-manager/buttons/lid_ac "nothing"
```

---

