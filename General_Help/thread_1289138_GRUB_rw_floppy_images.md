---
title: "GRUB r/w floppy images"
date: 2009-10-12
forum: General Help
---

### Post by mikeglover on 2009-10-12
I currently have GRUB installed on a USB stick.
I have several floppy img files on there and booting them using memdisk.
I need the disk to be Read / Write when I boot them.
Here is a example of the current menu.lst item I have:

```
title		RM Standard Build Disk
kernel 		/grub/memdisk
initrd		/images/RMStandard.img rw
```

rw tag doesn't seem to work. Anyone got any ideas?

---

