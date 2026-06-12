---
title: "How do I disable tooltips in Lubuntu?"
date: 2011-06-13
forum: General Help
---

### Post by Rytron on 2011-06-13
Hi.

How do I disable tooltips in Lubuntu? When I hover over icons on panel it gives a tooltip, I'd rather disable that feature.

Thanks.

---

### Post by gmargo on 2011-06-13
Taskbar tooltips appear to be configurable in Lubuntu, however I could not find a GUI dialog to adjust it.  But I did find the configuration file and was able to turn tooltips off.  See if this works for you:

Edit the file **$HOME/.config/lxpanel/Lubuntu/panels/panel**

Search for the string "tooltips=1" and change the 1 to 0.  

Then restart the desktop.

---

### Post by Rytron on 2011-06-13
> **gmargo said:**
> Taskbar tooltips appear to be configurable in Lubuntu, however I could not find a GUI dialog to adjust it.  But I did find the configuration file and was able to turn tooltips off.  See if this works for you:

Edit the file **$HOME/.config/lxpanel/Lubuntu/panels/panel**

Search for the string "tooltips=1" and change the 1 to 0.  

Then restart the desktop.

Thank you gmargo. I love this community. ;)

---

