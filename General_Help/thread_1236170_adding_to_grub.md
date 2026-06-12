---
title: "adding to grub"
date: 2009-08-10
forum: General Help
---

### Post by glennnf on 2009-08-10
Just wondering if it's possible to add my vista drive to grub or menu list.It is installed on a different drive to ubuntu & was installed with the ubuntu drive diconnected so grub would not detect it. I would like both drives to show up as boot options.Thanks.

---

### Post by merlinus on 2009-08-10
Post results of

```
sudo fdisk -l
```

and indicate which hdd and partition is vista.

Also, what is boot order of hdds in bios, and check to make sure that /boot/grub/device.map matches this.

---

### Post by glennnf on 2009-08-12
Hi Merlin,thanks for the reply ,here is the output from sudo fdisk-l.Device map shows(hd0)/dev/sda & bios set correctly. Vista is on dev/sda1-/dev/sdb,does that look right?Thanks,Glennnf

---

