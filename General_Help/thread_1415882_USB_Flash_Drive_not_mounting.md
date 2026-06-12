---
title: "USB Flash Drive not mounting"
date: 2010-02-25
forum: General Help
---

### Post by PeteUplink on 2010-02-25
My USB flash drive has stopped working with Ubuntu. 

Normally when I remove it I unmount it first, but the last time I just unplugged it. After I unplugged it, it started not working.

When I put it in a windows machine, it shows up as drive E: but says "no disk" when I try to access it.

 In my Ubuntu machine I can see it as USBDrive under Places > Computer, but it's unmounted. When I click mount nothing happens.

Can it be made to work or is it dead?

---

### Post by cdenley on 2010-02-25
I'm guessing it is corrupted. Are there any important files on it? If so, create an image of the corrupted data on the drive so that files may be recovered. If not, simply re-format it. In ubuntu, you can use gparted.

---

### Post by c9-3Rr0r on 2010-02-25
Try use 

```

sudo fsck /dev/yourflashdrive

```

---

