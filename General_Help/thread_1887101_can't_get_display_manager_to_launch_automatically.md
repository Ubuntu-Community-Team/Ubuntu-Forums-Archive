---
title: "can't get display manager to launch automatically"
date: 2011-11-26
forum: General Help
---

### Post by foodmonkey on 2011-11-26
had a stable 11.10 running - installed the updates and no splash or login screen

did a purge of flgrx and reconfigure of xserver

restarted - still going straight to terminal

did reconfig of lightdm - istalled startupmanager

can login in using my userid as then lightdm start - back where i used to be - all the tweaks are still there.

what step am i missing between boot and a terminal display - shouldn't the greeter screen come up by default and please, please where to i find the setting for this?

any help appreciated - i was nearly at the point of doing a complete reinstall and losing some recently uploaded pictures - i would have been toast from the missus if that had happened

from reading i'm thinking it maybe something to do with the grub settings and i'm not sure how those work.

---

### Post by HumbleNoob on 2011-11-27
Hi Foodmonkey,

Could the problem be related to *lightdm*?

Could you try to install GDM as default desktop manager (you can always revert back to ligthdm with: *sudo dpkg-reconfigure lightdm* ) and see if there is any improvement?


```

$sudo apt-get install gdm

```

---

