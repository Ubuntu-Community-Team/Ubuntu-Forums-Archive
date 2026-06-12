---
title: "Firefox doesn't see mozplugger"
date: 2009-12-21
forum: General Help
---

### Post by FreeFull on 2009-12-21
Mozplugger is installed, but when I check Firefox's plugin list it does not appear. I have checked and mozplugger.so is in the same place as other plugins, but the other plugins do show up.

---

### Post by lovinglinux on 2009-12-21
Close Firefox, then find you profile folder, which should be under ~/.mozilla/firefox, then delete the file **pluginreg.dat** and restart Firefox. This should fix problems with plugins not showing up on the plugin list of FF.

---

### Post by FreeFull on 2009-12-21
I already did that before seeking help. It turned out that removing the pluginreg.dat from ~/.mozilla/firefox did not help. What I did was use locate to find all instances of pluginreg.dat and deleted them. I have also purged and reinstalled mozplugger (after backing up the configuration). This fixed my problem.

---

