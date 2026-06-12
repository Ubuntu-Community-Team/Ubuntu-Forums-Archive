---
title: "Partition wont mount!!!"
date: 2010-12-27
forum: General Help
---

### Post by ben92 on 2010-12-27
I turned on netbook and grub wouldnt boot into ubuntu 10.10....i have a dual boot and windows works just fine. I've tried mounting on livedisk but it wont work, it wont let me run any checks or sudo fsck or anything.... can anyone help?? in dire need of a bit of help :)

---

### Post by Bucky Ball on 2010-12-27
Try booting into the recovery kernel (just below the regular one in the boot menu) and see what errors you can pick up, particularly where/when it hangs.

---

### Post by ben92 on 2010-12-28
> **Bucky Ball said:**
> Try booting into the recovery kernel (just below the regular one in the boot menu) and see what errors you can pick up, particularly where/when it hangs.

hey
when i go into recovery mode i get the same result....im told no init found and end up in busybox

---

### Post by Bucky Ball on 2010-12-28
Do you end up in busybox as root at a cursor?

If so, try:

```
startx
```

---

