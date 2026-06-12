---
title: "Disable password prompt after hibernation"
date: 2009-11-07
forum: General Help
---

### Post by Stuart P. Bentley on 2009-11-07
How do you make it so that, after you turn the machine back on after Hibernate, instead of prompting for your password, it just goes straight to your desktop?

---

### Post by Stuart P. Bentley on 2009-11-07
Found the answer in an old thread. Here it is for 9.10:

Run gconf-editor (Alt+F2 brings up the run dialog). Navigate to apps/gnome-power-manager/lock. Here you will find all of the lock-related settings.

---

