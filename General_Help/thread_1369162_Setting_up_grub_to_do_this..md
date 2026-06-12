---
title: "Setting up grub to do this."
date: 2009-12-31
forum: General Help
---

### Post by dragos240 on 2009-12-31
Hi, I have a gentoo system, and I use it a lot, however, sometimes I boot into ubuntu. I want grub to have an an option where it boots from ubuntu's grub. I loaded grub2 into /dev/sdb1, so my normal bootloader was untouched, I made grub boot into /dev/sdb1, by doing this:
root (hd1,0)
chainloader +1

Well it worked, but when I was using grub-install, it said that booting into a partition is not the best idea, and that it uses blocklists which are unreliable. Is there a better way of doing this?

---

### Post by Leppie on 2009-12-31
if /dev/sdb is ubuntu only, you can install grub2 to the mbr of /dev/sdb and then have grub legacy chainload grub2 from there.
or use 1 grub for all systems.

---

### Post by oldfred on 2009-12-31
as leppie says chainboot from the MBR of sdb.

root (hd1)
chainloader +1

From ubuntu you can run this to reinstall grub2 to sdb
sudo dpkg-reconfigure grub-pc

---

### Post by Leppie on 2009-12-31
> **oldfred said:**
> From ubuntu you can run this to reinstall grub2 to sdb
sudo dpkg-reconfigure grub-pc

or:
```
$sudo grub-install --recheck /dev/sdb
```

---

### Post by dragos240 on 2009-12-31
Why didn't I think of that before >.<. Solved.

---

### Post by Leppie on 2009-12-31
> **dragos240 said:**
> Why didn't I think of that before >.<. Solved.

sometimes the easiest solutions come to mind last...

---

