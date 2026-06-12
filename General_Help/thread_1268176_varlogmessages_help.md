---
title: "/var/log/messages help"
date: 2009-09-16
forum: General Help
---

### Post by gbrethen on 2009-09-16
I keep seeing this in my /var/log/messages:

kernel: Inspecting /boot/System.map-2.6.28-14-generic
kernel: Cannot find map file.

is this a problem?  If so, how do I fix it?

I have tried to find a System.map file, but nothing.  I do see System.map-2.6.28-14-generic file.

Any help appreciated.  I have spent a few hrs searching and googling, but to no avail!

---

### Post by dcstar on 2009-09-18
> **gbrethen said:**
> I keep seeing this in my /var/log/messages:

kernel: Inspecting /boot/System.map-2.6.28-14-generic
kernel: Cannot find map file.

is this a problem?  If so, how do I fix it?

I have tried to find a System.map file, but nothing.  I do see System.map-2.6.28-14-generic file.

Any help appreciated.  I have spent a few hrs searching and googling, but to no avail!

Either reinstall the 2.6.28-14 kernel packages or install the 2.6.28-15 kernel from the jaunty-updates repository.

---

