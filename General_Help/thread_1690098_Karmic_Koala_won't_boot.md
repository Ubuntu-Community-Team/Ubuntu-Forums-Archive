---
title: "Karmic Koala won't boot"
date: 2011-02-17
forum: General Help
---

### Post by inoh on 2011-02-17
am running Ubuntu 9.10 on my laptop via USB external HDD.  Currently it will not boot.  I get the logo followed be an immediate filesystem check.  At 90% complete it check crashes followed by the following:

init: mountall main process (500) terminated with status 3
Mount of filesystem failed.
A maintenance shell will now be stated.
CONTROL-D will terminate this shell and re-try.
root@c-desktop:~#

How do I go about fixing this?

---

### Post by inoh on 2011-02-22
I found that most of these errors occur after updates, as did mine, forgot to mention.  I booted with a live CD and found there is not menu.lst in the boot/grub directory.  Where can I get a copy of this file?

---

