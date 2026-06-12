---
title: "Black screen when user logs out"
date: 2010-08-21
forum: General Help
---

### Post by StevenSteavis on 2010-08-21
I've searched the web and these forums and I don't seem to be the only one with this problem yet I couldn't find a cure for it; 2 users are logged in, one of them logs out and the screen goes blank. Nothing works except shutting off the computer manually.

Does anyone know if a cure has been found for this problem by now?

---

### Post by StevenSteavis on 2010-08-22
No one?

---

### Post by dino99 on 2010-08-22
you can do two things:

- watch errors logged to help you (system->admin->logviewer, .xsession-errors (unhide with ctrl+h))

- use the latest xserver packages from that ppa:
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates](https://launchpad.net/~ubuntu-x-swat/+archive/x-updates)

to go forward, you can file a bug on launchpad by running into a terminal: sudo ubuntu-bug thexservernameused

some doubts about plymouth too, boot without "splash" to know if it make difference (if grub menu i hidden, at end of bios process , hold "shift" key down to see it, then you can edit the boot line and remove "splash" and boot (ctrl+x))

---

