---
title: "Last upgrade broke my Nvidia driver"
date: 2011-01-15
forum: General Help
---

### Post by micheledm on 2011-01-15
Yesterday I made some daily upgrades to my Ubuntu and played some Minecraft. Today i turned on my pc and everything that uses Nvidia driver seems to be broke. I can boot to GUI with "nvidia" driver in xorg.conf and even the  annoying Nvidia logo appears before logon screen, but then  for example in gnome docky is not able to start in compositing mode and Minecraft crashes because of some 3D graphic error.

I've never installed Nvidia driver from repository, always from the package provided by Nvidia. I tried to install it again and it prompt me the following error: "File /usr/lib/xorg/modules/extensions/libglx.so is not a symbolic link" but after that it goes on with the installation without any further error, but still no effect.

I have a dell xps1330m with Nvidia 9200M.

Thank you!

---

### Post by marin123 on 2011-01-15
i had similar problems with my ati graphic card after upgrading xorg. i found the solution in reinstalling the drivers for graphic card.

---

### Post by marin123 on 2011-01-15
sorry for the double post... :(

---

### Post by micheledm on 2011-01-15
i did it, but it did not solved my problem :(

---

