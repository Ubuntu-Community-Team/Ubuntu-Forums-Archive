---
title: "Upgrade to 12.04; fan running constantly"
date: 2012-04-29
forum: General Help
---

### Post by OllieGab on 2012-04-29
After upgrading from 11.10 to 12.04 the on-board fan is running at full speed constantly. Two other OSs on my machine do not cause this problem, including Ubuntu before the upgrade.
So is this a setting problem? Some packages missing? If I were to (have to) download some propitiatory drivers; how would I go about to do that?
any suggestions?

Cheers

---

### Post by OllieGab on 2012-05-01
After some additional investigation I have found the following:
the fan running 'like the clappers' was the graphics card fan.
It turned out that the "use the Nvidia driver" in the /etc/X11/xorg.conf file was commented out.
I believe this could easily have been sorted out by manually editing the file (?) but as it happens running the 'nvidia-configure' (or was it 'nvidia-update'?) it automatically changed the content of that file (and made a back-up of the earlier version).
So now it works fine!
I do have a similar problem with Debian but that's another story!

Cheers

---

