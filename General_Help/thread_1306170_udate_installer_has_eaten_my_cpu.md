---
title: "udate installer has eaten my cpu"
date: 2009-10-30
forum: General Help
---

### Post by eheitner on 2009-10-30
Hi-
I am running 9.04 on my dell laptop. When I log in, the desktop starts as normal, but within a few seconds my CPu usage monitor notes that I am using 100% of my memory and I haven't started any programs running yet. 

From this state I can't open any programs. Terminal and update monitor will open a dialog window bt not load completely. Trying to open system monitor to shut down whatever program is doing this doesn't work; system monitor starts to open but then shuts itself down.

I think the atomatic updater is responsible, because when I log out, it tells me it can't because automatic updater is still rnning. I can force it to quit at that point and log out.

Is there something i can run to fix this?

---

### Post by hwttdz on 2009-10-30
Try using the failsafe gnome session and updating/upgrading from there.  You might also top and see if there's anything running there.

---

### Post by eheitner on 2009-10-30
Hi- upgraded the installation from the failsafe terminal and that appears to have fixed it. Thanks!

---

### Post by hwttdz on 2009-10-30
It strikes me that a lot of these problems may stem from the huge load on the servers the day the upgrade is released, especially since most people don't change their server from the main server.  Then people get incomplete upgrades and all sorts of problems.  Granted this release seems to have some real bugs in it.

---

