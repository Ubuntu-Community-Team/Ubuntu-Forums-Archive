---
title: "Ubuntu 11.10: Can't set panel to opaque anymore"
date: 2012-01-28
forum: General Help
---

### Post by veroslav on 2012-01-28
Hi,

I am running Ubuntu 11.10 and I am using CompizConfig Settings Manager to adjust the panel opacity (CCSM->Ubuntu Unity Plugin->Experimental->Panel Opacity).

However, this morning, after messing whith the system and restarting the computer, I could no longer set the panel opacity to fully opaque in CCSM. Even though the value is set to 1.0000, the panel is semi-transparent (see attached image). I've also attached some screenshots that show the panel appearance when using the lower opacity values (0.9930 and 0.5012).

What I did previous to this problem was to uninstall the overlay scrollbars by issuing the following:

```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar3-0.2-0 liboverlay-scrollbar-0.2-0
```I also added the gnome-sushi by issuing the following:

```
sudo apt-get install gnome-sushi
```After I restarted the computer having done the above, the panel no longer was opaque, and no changes I do in CCSM can get it to be opaque.

Could anybody help me fix this issue?

Thanks in advance!

Kind Regards,
Veroslav

---

