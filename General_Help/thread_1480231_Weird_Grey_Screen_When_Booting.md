---
title: "Weird Grey Screen When Booting"
date: 2010-05-11
forum: General Help
---

### Post by mc_tux on 2010-05-11
I've installed 10.04 and it worked fine. Then I wanted to update NVIDIA drivers to the latest version, so I've downloaded them from NVIDIA's site and successfuly installed. After reboot, had to use low-graphics mode. Uninstalled nvidia drivers from package manager. Well, I've messed everything up.
Now I reboot the PC, grub loads, I select Ubuntu and after a few seconds, the screen goes from black to very weird, something like color stripes with no shape, then, after a few more seconds it just goes completely grey, like my monitor would be broken.
I thought the Live CD would help me, so I boot it, then the black screen appears with some purple icons at the bottom. After a few seconds - grey screen again.
The same with Ubuntu Rescue Remix CD.
Why? How could I recover my system? Shouldn't some menu appear when booting from Live CD?

---

### Post by Sef on 2010-05-13
How did you resolve the problem?   Please post so that others may benefit from your experiences.   Thank you.

---

### Post by mc_tux on 2010-05-13
I hadn't solved the problem yet.

---

### Post by mc_tux on 2010-09-24
OK so after half a year I finally found the answer. It turns out to be a bug or not a bug, related to nouveau+nvidia. To fix it, you have to add nouveau.modset=0 when booting (in grub, press "e") or edit the file /boot/grub/grub.

---

