---
title: "Booting Problem"
date: 2006-03-23
forum: General Help
---

### Post by Bakerconspiracy on 2006-03-23
I have a dell inspirion 8600 with dual boot ubuntu/windows. I was working fine last night but this morning when I turn it on I get through the bios fine until it goes to load grub. About a fraction of a second after it is done with the bios it immediately turns off and begins to restart. I get to see grub v1.5 for a split second before it shuts off. Last night the only thing I did was install the RPM package (Red Hat Package Managment) and shut it down. I don't know if im right but I think there is either something wrong with grub or my run level is being switched to 6 every time I boot up. I guess this could also be a hardware problem but it doesn't seem so... Any suggestions are appreciated.

---

### Post by Ramses de Norre on 2006-03-23
Can you boot from the live cd?
If so try to check the default runlevel in /etc/inittab (but that shouldn't change automaticaly).
You could also try to reinstall grub [https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")
A hardware problem seems odd to me, I think that should occur in a later state of the boot process (bu it is possible though).

---

