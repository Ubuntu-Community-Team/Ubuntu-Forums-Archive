---
title: "How to detect &amp; create a swap file/partition?"
date: 2010-01-26
forum: General Help
---

### Post by pstein on 2010-01-26
I am sitting in front of an Ubuntu which was installed previously by someone else. 
How can I find out if a swap partition was defined?
Is it always a swap partition or only a (ONE) swap file (like in Windows XP) ?
 
If there is currently no swap partition: How can I create one and tell Ubuntu to use it?
 
How can I conversely tell Ubuntu NOT to use a separate swap partition but to use 
the directory /swp instead?
 
Peter

---

### Post by audiomick on 2010-01-26
Hallo
```
sudo fdisk -l
```
should tell you what you have, I think.
That is a lower case L on the end, not a figure one.
Post the ouput back here if you don't understand it.

---

### Post by t4thfavor on 2010-01-26
Look at the output of free -m, and it should have a line that says

```

-/+ buffers/cache:        113       1393
Swap:         4408          0       4408

```

or without swap
```

-/+ buffers/cache:        111       1395
Swap:            0          0          0

```

To create one, you make a new partition on a hdd, and make it of type linux swap. 

then you add a line to your /etc/fstab to show the system where the new swap is.

That line is already there if you have swap, if not it will look something like this:

```

# swap was on /dev/sda5 during installation
UUID=9d94c3b3-57fb-440b-b1ca-2ee32c34640d none            swap    sw              0       0

```

---

