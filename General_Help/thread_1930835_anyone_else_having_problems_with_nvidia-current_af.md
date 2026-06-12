---
title: "anyone else having problems with nvidia-current after recent updates on 11.10?"
date: 2012-02-24
forum: General Help
---

### Post by DukeBoxer on 2012-02-24
After recent updates (within the last 5 days) I've been having issues with unity and gnome shell and the nvidia-current driver. I haven't fully researched it yet but the screen flickers when I change windows in shell and when I open the dash in unity. There are no problems in unity 2d or gnome with no effects. I have a nvidia gtx460 video card. These problems just started showing up, before I was running it with dual monitors and it worked perfectly. Any help on troubleshooting this problem would be appreciated!

---

### Post by DukeBoxer on 2012-02-24
Forgot to say that when I do try to switch windows or open the dash, Xorg pins the CPU at 100+%

---

### Post by DukeBoxer on 2012-02-24
Solved this one.Just uninstalled and re-installed the nvidia-common and nvidia-current. I'm thinking the DKMS didn't get updated with the new kernel (3.0.0-16) that got updated the other day

---

