---
title: "Ubuntu 10.4 checks disks after every boot"
date: 2010-05-15
forum: General Help
---

### Post by dchaley on 2010-05-15
Ever since my upgrade from 9.10 to 10.4, every time I reboot the system it does a full disk check. /var/log/boot.log tells me that fsck thinks that the file systems contain errors or that it wasn't cleanly unmounted. And yet, it doesn't seem to actually find errors, and a clean reboot starts another check (again with it thinking something is dirty). I dual-boot with Windows, and reboot from there with the same problem.

Again, all of this is new with 10.4 and was not happening with 9.10.

Any ideas? Is there a way to find out when/how/why the disks are not being unmounted cleanly?

Thanks in advance.

---

### Post by TeoBigusGeekus on 2010-05-15
Boot up with a live cd and do a fsck on your drives.

---

### Post by VincenzoDentamaro on 2010-05-15
I have the same problem.
In my pc I have installed ONLY Ubuntu 10.4, I have done one partition for boot, one partition for the home directory, one partition for root / and one swap partition.

Why it doesn't unmount my disks correctly?

---

### Post by damphoud on 2010-05-27
Bump :popcorn:

---

### Post by dcstar on 2010-05-27
> **dchaley said:**
> 
........
Any ideas? Is there a way to find out when/how/why the disks are not being unmounted cleanly?

Thanks in advance.

Look in the syslog file.

---

