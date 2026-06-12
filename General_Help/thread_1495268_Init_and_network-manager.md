---
title: "Init and network-manager"
date: 2010-05-27
forum: General Help
---

### Post by Praxicoide on 2010-05-27
Hi guys. I just updated from 9.04 to 9.10 (it's a [long story](http://ubuntuforums.org/showthread.php?t=1401228), and I still can't go beyond 2.30).

The update got rid of WICD, which is what I used and installed network-manager. Network-manager was not working at all, so I uninstalled it again and installed WICD. I could connect perfectly and had no problems.

However, now the computer hangs during boot, saying that init can't start network-manager. I assume that something went wrong during the uninstalling process, since it wasn't updated.

This is the message:

init: Failed to spawn network-manager main process: unable to execute: No such file or directory.

So how do I update it or manually change it so it stops requesting network-manager?

Thank you in advance

---

### Post by Naitsirhc Hsem on 2010-05-27
try looking in 

System>Preferences>Startup Applications

---

### Post by Praxicoide on 2010-05-27
OK, if I can get past the boot-up, I'll try that.

No. Can't. I tried with an older kernel, and made to X, but it broke down right away.

---

### Post by Praxicoide on 2010-05-27
Here's something else:

Warning: unable to find a suitable fs in /proc/mounts, is it mounted?
Use --subdomainsfs to override.

---

