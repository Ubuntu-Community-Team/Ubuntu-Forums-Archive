---
title: "Folders stopped working"
date: 2010-04-28
forum: General Help
---

### Post by LoonQ on 2010-04-28
Hi

After I deleted som movies in homefolder all graphical folders stopped responding. It does not matter if its homefolder, network folders, or computer. It is quiet strange.. anyone got any idea how to get the functionalityh back without reinstalling?

---

### Post by Sin@Sin-Sacrifice on 2010-04-28
Umm... not sure exactly what you're asking but I think you just need to restart nautilus. Might as well restart gnome. Press ctrl+alt+F2 and log into the CLI. Type ```
sudo service gdm restart
``` then log back into your desktop and see if the problem is still happening.

---

### Post by LoonQ on 2010-04-28
Tried to shutdown and restart but still the same problem. I´m quit low on discspace can that problem cause this?

---

### Post by lidex on 2010-04-28
Try this terminal command:
```
rm -r ~/.local/share/gvfs-metadata
```

Terminal="Applications->Accessories->Terminal"

---

