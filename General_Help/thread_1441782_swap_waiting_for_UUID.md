---
title: "swap waiting for UUID:"
date: 2010-03-29
forum: General Help
---

### Post by Tom_T on 2010-03-29
I've just upgraded my wife's netbook to UNR 9.10
This seemed to go well and the netbook has been working fine since.

Yesterday my daughter used the netbook with out any issues, but when my wife tried it halted during boot with:

Swap waiting for UUID: xxxxxxxxxxxxxx

After a couple of reboots it started working fine, but looking at /etc/fstab the entry for swap is different to the UUID shown in blkid

Do I just update fstab with the UUID from blkid ??

Thanks :)

---

### Post by vanadium on 2010-03-29
> Do I just update fstab with the UUID from blkid ??
Yes.

---

### Post by Tom_T on 2010-03-31
Thanks Sorted :)

---

