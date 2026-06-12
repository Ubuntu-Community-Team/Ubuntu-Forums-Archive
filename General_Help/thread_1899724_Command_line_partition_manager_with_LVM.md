---
title: "Command line partition manager with LVM"
date: 2011-12-24
forum: General Help
---

### Post by Bradburts on 2011-12-24
Hi,
Need to partition SD cards with FAT, ext4 and swap.
ext4 should use LVM. mdadm capability would be nice as well.
 
My understanding is that Gparted won't be reliable with LVM.
Any suggestions?
What does the installer use?

---

### Post by Lars Noodén on 2011-12-24
Well, if you're looking to work with the shell, then [parted](http://manpages.ubuntu.com/manpages/oneiric/en/man8/parted.8.html) is your choice.  It works with LVM.

---

