---
title: "I/O errors on basicly everithing"
date: 2010-08-18
forum: General Help
---

### Post by groovy354 on 2010-08-18
After instalation (when I hit 'restart') there was a lot of I/O errors. Now whenever I try to install deb package or even run Synaptics package manager, it always shows some i/o errors... I can't do anything! Help!

---

### Post by Grenage on 2010-08-18
Check your Hard Drive and RAM, you've likely got hardware issues.

---

### Post by groovy354 on 2010-08-18
But I can copy, create files etc...

---

### Post by ronnielsen1 on 2010-08-18
> But I can copy, create files etc... 	
> Check your Hard Drive and RAM, you've likely got hardware issues.

Use memtest to check the memory and Hirens boot cd has a lot of useful utilities to check the hard drive. I/O errors means it can't read the source

---

### Post by endotherm on 2010-08-18
> **groovy354 said:**
> But I can copy, create files etc...
nothing to do with it. boot from a live cd and do a disk check with 
```
sudo fsck <devicename>
```

---

### Post by sydbat on 2010-08-18
I would also suggest turning the computer off, unplugging it, opening the case and checking all the connections. Something might have come loose.

---

### Post by anubhavrocks on 2010-08-18
> **groovy354 said:**
> After instalation (when I hit 'restart') there was a lot of I/O errors. Now whenever I try to install deb package or even run Synaptics package manager, it always shows some i/o errors... I can't do anything! Help!

Can you copy the error logs.That will be helpful in understanding the problem you are facing.

---

### Post by groovy354 on 2010-08-18
I'll post logs as soon as I'll get acces to that pc

---

