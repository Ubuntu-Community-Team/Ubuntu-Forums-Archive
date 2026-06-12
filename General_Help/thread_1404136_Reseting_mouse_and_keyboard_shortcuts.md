---
title: "Reseting mouse and keyboard shortcuts?"
date: 2010-02-11
forum: General Help
---

### Post by rockerex on 2010-02-11
I am very new to Ubuntu and I made a mistake while changing the shortcuts for zoom in compiz config settings manager. Now the shortcuts for both of keyboard and mouse are so messed up... My right arrow key does not work and my middle click cannot scroll =((( 

i tried setting back to defaults in the compiz manager, changing accounts, stopping compiz . all to no avail.

How do I reset the shortcuts to default? :-(:-(

---

### Post by Andreas1 on 2010-02-11
try this (in a terminal):

```
gconftool --recursive-unset /apps/compiz
```

although, aren't there also reset buttons next to each option in compizconfig-settings-manager?

---

