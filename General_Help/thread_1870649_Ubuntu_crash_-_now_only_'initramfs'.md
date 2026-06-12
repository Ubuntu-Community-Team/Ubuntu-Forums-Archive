---
title: "Ubuntu crash - now only 'initramfs'"
date: 2011-10-27
forum: General Help
---

### Post by scirwin on 2011-10-27
My Ubuntu (most recent version as of August '11) crashed and only brings up the 'initramfs' terminal at bootup. (see attached screenshot). 

How it happened: left computer on for a long time, the screensaver came on, then the screen went black. Could not awaken, so I did a hard turn-off.

Can I rescue this?

Thanks!

---

### Post by matt_symes on 2011-10-27
Hi

It looks like something has gone bang inside your initramfs file. Maybe one of the modules. 

Do you have any special setup like encrypted partitions, raid or lvm ?

First try to boot into an older kernel if you have one. Can you do that ?

If you can't then boot into a liveCD/USB and check the filesystem using fsck from a terminal.

Kind regards

---

