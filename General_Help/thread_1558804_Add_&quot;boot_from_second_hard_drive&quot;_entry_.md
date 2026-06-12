---
title: "Add &quot;boot from second hard drive&quot; entry to GRUB2"
date: 2010-08-22
forum: General Help
---

### Post by Asmodai on 2010-08-22
I'm using GRUB2 on my main drive and I have a second hard drive where  GRUB is also installed on. Now when I want to boot from the other HD, I  need to switch boot order in the BIOS every time, which is unconvenient.  So I want an entry in GRUB that simply boots from the other hard drive (i.e. "switches" to the other GRUB).

I should be able to add a new entry to GRUB by editing /etc/grub.d/40_custom...
however, I don't know much about GRUB and came up with the following:

```
menuentry "Boot from second hard drive" {
    set root=(hd1)
    chainloader +1
}
```But I don't know if that'll work. Can I just omit the partition for set root like this?
Do I need to add anything else?

---

### Post by Asmodai on 2010-08-22
Found a different solution:
I added "(hd1)    /dev/sdb" to /boot/grub/device.map and ran update-grub.
This adds to operating systems on the second drive to GRUB, which works just as well.

---

