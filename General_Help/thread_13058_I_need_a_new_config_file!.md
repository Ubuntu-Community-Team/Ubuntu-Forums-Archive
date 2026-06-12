---
title: "I need a new config file!"
date: 2005-01-28
forum: General Help
---

### Post by andrew-irl on 2005-01-28
Hi, 

I was messing around with the XF86Config-4 file, X wouldn't start on reboot..

I replaced the file with a version from the live cd, stupidly forgetting to back it up.

X works but it isn't configured correctly for my system.

My question:

Is there any way to restore the config file for my system without a reinstall?

Thanks

---

### Post by az on 2005-01-28
This is not windows.  Of course you do not need to reinstall.

sudo dpkg-reconfigure xserver-xfree86

---

### Post by andrew-irl on 2005-01-29
[QUOTE=azz]This is not windows.  Of course you do not need to reinstall.

sudo dpkg-reconfigure xserver-xfree86[/QUOTE]
 I reconfigured X but fullscreen video is still pixelated. (This was working fine before). :(

---

### Post by az on 2005-01-29
What is pixelated?

---

