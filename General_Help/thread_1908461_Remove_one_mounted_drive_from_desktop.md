---
title: "Remove one mounted drive from desktop"
date: 2012-01-13
forum: General Help
---

### Post by Kreeyon on 2012-01-13
Hi,

I have selected in Ubuntu 11.10 to have all mounted drives appear on the desktop and for most cases this is fine.  When plugging in an external USB drive or plugging in my phone I want the drives to show up on the desktop for easy management.

The problem I have is that I have now installed a second hard drive into my desktop for media purposes and have changed the settings so that the drive is mounted automatically when Ubuntu boots, my question is, can I have all drives apart from this one hard drive show up on the desktop?  Is it possible to just hide this one hard drive icon from showing on the desktop when it's mounted?

---

### Post by Double.J on 2012-01-13
> **Kreeyon said:**
> Hi,

I have selected in Ubuntu 11.10 to have all mounted drives appear on the desktop and for most cases this is fine.  When plugging in an external USB drive or plugging in my phone I want the drives to show up on the desktop for easy management.

The problem I have is that I have now installed a second hard drive into my desktop for media purposes and have changed the settings so that the drive is mounted automatically when Ubuntu boots, my question is, can I have all drives apart from this one hard drive show up on the desktop?  Is it possible to just hide this one hard drive icon from showing on the desktop when it's mounted?

Hi there, I assume by setting up automount you mean you made an entry for it in /etc/fstab?. and it's currently mounted at /media or /home?

You just need to have it mount somewhere else, such as /mnt? you could also creaes a directory specialy for it to mout in, that's what I do for my data partition, -it's not very *nix-y but I have a /Data directory as it keeps things simple for me. To the best of my knowledge drives set to mount at /media and /home will be displayed on the desktop if "volumes displayed" is selected in gconf - so the answer is just mount it somewhere else :)

---

### Post by Kreeyon on 2012-01-15
That worked thanks

---

