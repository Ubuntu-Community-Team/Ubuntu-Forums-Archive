---
title: "Package Manager Broken"
date: 2011-01-10
forum: General Help
---

### Post by Coding Monkey on 2011-01-10
Hi Guys

I recently had to format my hard drive.  After formatting, I reinstalled Ubuntu and updated it to 10.04.  After the update, I installed a couple of applications (including the fglrx drivers for my ATI HD2600).

I'm not sure what, but something appears to have broken my package manager.  When I open the update manager, I get the following message - "It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first."

When I run "sudo apt-get install -f" I get the following;

```
Removing fglrx ...
dpkg-divert: mismatch on package
  when removing `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by fglrx'
  found `diversion of /usr/lib/libGL.so.1.2 to /usr/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx'
dpkg: error processing fglrx (--remove):
 subprocess installed post-removal script returned error exit status 2
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Errors were encountered while processing:
 fglrx

```

Any help on fixing this will be much appreciated.

Thanks!

---

### Post by Coding Monkey on 2011-01-10
Bump...

---

### Post by Coding Monkey on 2011-01-10
For future reference - I resolved the issue by **reinstalling** fglrx via Synaptic.  It gave errors on a previous attempt to **uninstall** fglrx.

---

