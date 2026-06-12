---
title: "sudo: unable to resolve host ..."
date: 2009-08-06
forum: General Help
---

### Post by boondocks on 2009-08-06
On a Ubuntu 8.04 Desktop system, I had to
change the hostname from Zebra to Kangaroo.

I only had ssh access.
So I changed the name in "/etc/hostname".
Then rebooted the system.
It works.  The new hostname is Kangaroo.

But now whenever I want to do any "sudo ..." it says:
sudo: unable to resolve host Kangaroo

How do I fix this?

---

### Post by CatKiller on 2009-08-06
> **boondocks said:**
>  How do I fix this?

You need to change /etc/hosts as well. Since you can no longer use sudo, you'll need to either reboot into recovery mode or use the live cd to do so

(Recovery mode will automatically make you root, the live cd has a working sudo)

---

### Post by slakkie on 2009-08-06
See this thread: [http://ubuntuforums.org/showthread.php?t=1055393](http://ubuntuforums.org/showthread.php?t=1055393)

---

