---
title: "fglrx cannot be removed"
date: 2010-09-01
forum: General Help
---

### Post by Gaiwecoor on 2010-09-01
After a bit of trouble with an ATI card, I decided to swap it out for my old nVidia card.  All display devices are working fine.  However, the fglrx package is now permanently marked for removal, but an error occurs every time it tries to be removed.  This is now stopping me from installing/updating any packages.

From the command-line:
```
:~$ sudo apt-get remove fglrx
*snip*
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
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

I've looked through the forums, but only found information relating to xorg-driver-fglrx.  My system reports this as not being installed.

Any thoughts?

Thank you!

---

### Post by Autodidact on 2010-09-01
Maybe try to reïnstall and then remove?
You can always force removal with dpkg (although this is not recommended).

---

