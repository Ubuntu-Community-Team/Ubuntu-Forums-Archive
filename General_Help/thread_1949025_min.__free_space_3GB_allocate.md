---
title: "min.  free space 3GB allocate"
date: 2012-03-29
forum: General Help
---

### Post by saltcushy on 2012-03-29
hi gays.
I have small disk and I want change allocate 3gb free space in lubuntu 11.10.
Help me someone?;)

---

### Post by Bucky Ball on 2012-03-29
> **saltcushy said:**
> hi gays.

Priceless! You need to give a little more detail. If you can open a terminal (not sure how to get to that in 11.10 if it's running Unity) then input this and post the output back here:

```
sudo blkid
```That will let us know how you have your disk partitioned. ;)

Other option; boot from LiveCD (the CD you installed from), 'Try Ubuntu', when you are at the desktop, open Gparted (the partition manager), and expand the partition you need to into the 3Gb free space (but you will need to delete what is on the 3Gb first so you have 3Gb free space).

---

### Post by saltcushy on 2012-03-29
I don't want changing size partition. The operating system blocking write to the drive when get less then 3GB(free space) i want change  it eg. to 500MB
By the Way my partition ext4 it 63GB

---

### Post by Bucky Ball on 2012-03-29
If I am understanding you; I don't know if changing that limit is possible. The system needs a bit of headroom and if you only have 3Gb (your drive is almost full) that is about the headroom.

I suggest either deleting a few Gb or saving it off to an external device ...

---

