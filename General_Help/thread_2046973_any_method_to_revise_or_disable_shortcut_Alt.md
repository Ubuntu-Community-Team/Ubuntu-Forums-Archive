---
title: "any method to revise or disable shortcut Alt"
date: 2012-08-23
forum: General Help
---

### Post by pqsbbs on 2012-08-23
i'm using ubuntu 12.04 with unity desktop, is there any method to revise or disable shortcut Alt? when Alt is pressed, a command input panel pops up, it is convinent. however, when i want to swith from one app window to another app window with Alt+Tab, the command input panel pops up unexpectedly.   i know when i press Alt+Tab very carefully, this doesn't happen, but if the shortcut Alt can be reviced or disabled, it will be better.

thanks in advance

---

### Post by stinkeye on 2012-08-24
Install ccsm.
In the terminal...
```
sudo apt-get install compizconfig-settings-manager
```

Enter **ccsm** in the dash. Press Enter.

ccsm > Ubuntu Unity Plugin > behaviour
and disable the **Key to show Hud**.

---

