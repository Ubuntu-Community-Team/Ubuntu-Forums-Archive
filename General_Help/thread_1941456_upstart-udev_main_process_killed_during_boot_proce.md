---
title: "upstart-udev main process killed during boot process"
date: 2012-03-15
forum: General Help
---

### Post by brainwash on 2012-03-15
Hi,

I noticed some strange dmesg log entries today (haven't checked dmesg for quite a while).

Are these entries maybe related to the fix available on [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/829980](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/829980) (comment 32)? Can I simply ignore them?

> init: upstart-udev-bridge main process (497) killed by ABRT signal
init: upstart-udev-bridge main process ended, respawning
init: upstart-udev-bridge main process (661) killed by ABRT signal
init: upstart-udev-bridge main process ended, respawning
...
init: upstart-udev-bridge respawning too fast, stopped

Many thanks
brainwash

---

