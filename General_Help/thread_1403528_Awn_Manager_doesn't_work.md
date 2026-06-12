---
title: "Awn Manager doesn't work"
date: 2010-02-10
forum: General Help
---

### Post by iamjfarrell on 2010-02-10
My awn manager for the awn dock does not seem to want to open. I have tried to open it so I can configure my awn dock to work properly but it does not seem to want to co-operate. Should I uninstall and reinstall it or what?

---

### Post by iamjfarrell on 2010-02-10
Here is the output I get when I run "awn-manager" in the terminal.

```
 awn-manager
Traceback (most recent call last):
  File "/usr/bin/awn-manager", line 220, in <module>
    awnmanager = AwnManager()
  File "/usr/bin/awn-manager", line 136, in __init__
    self.prefManager = awnPreferences(self.wTree)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 109, in __init__
    self.setup_look(defs.BAR, defs.BAR_ANGLE, self.wTree.get_widget("look"))
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 363, in setup_look
    self.changed_look(dropdown)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 377, in changed_look
    self.reload_look(0, dropdown)
  File "/usr/share/avant-window-navigator/awn-manager/awnPreferences.py", line 368, in reload_look
    if self.client.get_int(defs.BAR, defs.BAR_ANGLE) == 0:
glib.GError: Type mismatch: Expected `int' got `float' for key /apps/avant-window-navigator/bar/bar_angle

```

---

### Post by hemimaniac on 2010-02-10
Are your desktop effects enabled?  In my endeavour to get awn working I had to set compiz to a flat composition backend

---

### Post by iamjfarrell on 2010-02-10
> **hemimaniac said:**
> Are your desktop effects enabled?  In my endeavour to get awn working I had to set compiz to a flat composition backend

Yeah, compiz is working and the awn dock works, it's just when I go to dock preferences or System > Preferences > Awn Manager nothing happens.

---

### Post by n0dix on 2010-02-10
Try:
sudo apt-get remove awn-manager --purge
sudo apt-get install awn-manager

---

