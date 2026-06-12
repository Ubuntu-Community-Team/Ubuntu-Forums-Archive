---
title: "libz.so.1 invalid ELF header, stuck on &quot;small dots&quot; startup screen"
date: 2010-12-25
forum: General Help
---

### Post by timcarson on 2010-12-25
Hi,

When I startup, the following happens:

1. I get the small dashing underscore at the upper left of the screen
2. A purple screen with "Ubuntu 10.04" and four pixel-sized dots appear.  The dots change from orange to white, but nothing else happens.

The purple screen is different from the screen that I normally booted up into.

When I select recovery mode from grub, some text flies by, then I get a blue screen with a selection of options: resume, clean, dpkg, failsaveX, grub, netroot, root.
If I resume, I get a tty.  However, there are many errors like this:

*Starting the winbind daemon winbind
/usr/sbin/winbindd: error while loading shared libraries: /lib/libz.so.1: invalid ELF header

Let me know what other information would be helpful.

EDIT: I fixed this by:

-Booting from a live CD
-Mounting my system partition from within the live CD boot
-Copying libz.so.1.2.3.4 from the live CD to my system partition

---

