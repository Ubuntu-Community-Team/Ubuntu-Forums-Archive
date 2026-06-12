---
title: "Boot Hang up, udev/udevmonitor/udevtrigger.conf errors"
date: 2010-01-18
forum: General Help
---

### Post by kruce on 2010-01-18
Ubuntu Server, x64, 9.10

I recently ran an apt-get upgrade, and now the darn thing won't complete its boot process.  It gets to a certain point, runs fsck on my system drive (but not my software raid drives), and hangs indefinitely.  The only clues I have are:

udev.conf : Input/Output error
udevtrigger.conf : Input/Output error
udevmonitor.conf : Input/Output error

fsck  ..... clean

...

nothing.


(I'm typing this from memory, not at the computer so the above lines are approximate).

In verbose mode, it looks like it calls the init-bottom script, but doesn't complete it.  For whatever reason, there isn't anything in the logs.

Also, I get the same result for recovery mode.  Does anybody have any idea about where I can go from here?

---

