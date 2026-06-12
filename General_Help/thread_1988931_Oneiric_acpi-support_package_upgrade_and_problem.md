---
title: "Oneiric: acpi-support package upgrade and problem"
date: 2012-05-28
forum: General Help
---

### Post by ratcheer on 2012-05-28
My daily upgrade on my Oneiric amd64 installation, this morning, upgraded one module, acpi-support. As part of the post installation setup, it issued the following warning:

> Setting up acpi-support (0.138.1) ...
update-rc.d: warning: /etc/init.d/acpi-support missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>

I tried to read the LSBInitScripts page at Debian, but it is all gobbledygook to me. Why was this module updated without apparently setting itself up, correctly? What, if anything, do I need to do?

Tim

---

### Post by Books on 2012-05-28
I'm showing the same message.

---

### Post by ratcheer on 2012-05-28
[https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/305587](https://bugs.launchpad.net/ubuntu/+source/acpi-support/+bug/305587)

I see the reasons, but I don't entirely understand them. The developers keep marking this bug with status "Won't fix". The bug was opened on 2008-12-05 and the most recent activity was on 2012-03-16 , so it has been ongoing for a long time.

Tim

---

### Post by ratcheer on 2012-05-28
Ok, by reading and experimenting, I got the warning to stop occurring by inserting the following code into file  /etc/init.d/acpi-support, after the first line:

```
### BEGIN INIT INFO
# Provides: linux-restricted-modules
# Required-Start: $local_fs
# Required-Stop:
# Default-Start: 2 3 4 5
# Default-Stop: 1
# Short-Description: Setup the linux restricted modules
# Description: Link the linux restricted modules at run time.
### END INIT INFO
```

I have no idea whether this is right or wrong, but it is working for me. Would someone with better knowledge of the problem please comment?

Tim

---

### Post by philinux on 2012-05-28
That's odd as a # normally signifies a comment only. I know grub is different maybe that file is too.

---

### Post by ratcheer on 2012-05-28
> **philinux said:**
> That's odd as a # normally signifies a comment only. I know grub is different maybe that file is too.

Yes, as the error message says, it is just looking for "LSB information". Apparently, the comments are the information it needs.

Tim

---

