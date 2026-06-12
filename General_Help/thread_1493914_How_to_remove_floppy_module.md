---
title: "How to remove floppy module"
date: 2010-05-26
forum: General Help
---

### Post by ssj6akshat on 2010-05-26
I disabled it in the BIOS and tried to remove it in the safe mode but that bloody thing is back everytime I log in.

Any help will be appreciated.

---

### Post by oshirowanen on 2010-05-26
I would like to know this too.  I have disabled the floppy drive from bios, but I still have it on the desktop places menu.  Probably the reason why my desktop takes a minute to appear.  10.04 seems to have a few very annoying bugs.

I hope these bugs are sorted out before 10.04.1.

---

### Post by dino99 on 2010-05-26
[http://www.ubuntugeek.com/tiphow-to-mountunmount-and-format-floppy-disk-in-ubuntu.html](http://www.ubuntugeek.com/tiphow-to-mountunmount-and-format-floppy-disk-in-ubuntu.html)

sudo gedit /etc/fstab

remove or comment with # above the line where you see fd0

---

### Post by philinux on 2010-05-26
> **ssj6akshat said:**
> I disabled it in the BIOS and tried to remove it in the safe mode but that bloody thing is back everytime I log in.

Any help will be appreciated.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/384579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/384579)

Disable the floppy module if all else fails.

---

### Post by oshirowanen on 2010-05-26
> **philinux said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/384579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/384579)

Disable the floppy module if all else fails.

What are the chances of this bug being corrected in time for 10.04.1?

---

### Post by ssj6akshat on 2010-05-27
> **philinux said:**
> [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/384579](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/384579)

Disable the floppy module if all else fails.

But How?I tried modprobe -r floppy and rmmod -f floppy and it says it is in use.

EDIT:Removing it from fstab and then rmmoding it worked!

---

