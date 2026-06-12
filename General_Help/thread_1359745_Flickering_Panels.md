---
title: "Flickering Panels"
date: 2009-12-20
forum: General Help
---

### Post by Pjstaab on 2009-12-20
After accidentally deleting my sound icon from the top panel my top and bottom panels close and then restart about once a second.  How can I stop this and how can I get my sound icon back?

---

### Post by Robbe_ on 2009-12-20
I had the same problem today also, problem started with suddenly 2 sound icons showed up, so I thought easy fix was to delete one of them.. didn't work so well. Both of them got deleted and the panel started going crazy.

Fixed it by doing this.

Delete the messed up panel (open a terminal a enter the below things)
1. sudo rm -r -f ~/.gconf/apps/panel

Restart X
2. sudo /etc/init.d/gdm restart

This restored the panel to a default, working state! :KS

---

### Post by Pjstaab on 2009-12-20
Thank you so very much.

---

