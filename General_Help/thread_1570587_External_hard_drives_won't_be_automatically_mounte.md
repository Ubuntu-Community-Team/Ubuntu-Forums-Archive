---
title: "External hard drives won't be automatically mounted after upgrading some packages..."
date: 2010-09-08
forum: General Help
---

### Post by jiapei100 on 2010-09-08
Hi, all:

1) Environment:
Ubuntu 10.04

2) Phenomenon:
External hard drives won't be automatically mounted after upgrading some packages...

I have a "not good" habit: I'd love to upgrade whatever suggested by Ubuntu upgrading center every morning.
However, after upgrading some packages for today, my computer won't be able to automatically mount external harddrives, including file systems ext4 and ntfs.


My question is:
1) How can I check what packages have been upgraded just within today?
2) How to make my Ubuntu be able to automatically mount external hard drives whenever I plug in a harddrive as before??


Best Regards
JIA

---

### Post by stee1rat on 2010-09-08
2) I think you can add another line to /etc/fstab to mount your hard drives at startup.

---

### Post by sharathcshekhar on 2010-09-08
> External hard drives won't be automatically mounted after upgrading some packages...

Are you able to mount them manually through 
```

mount /dev/sdXY /media 

```
I dont think updating your system would have caused any such problem. How ever you can check the upgrade history by going to 
synaptic > file > history

---

### Post by jiapei100 on 2010-09-08
Hi, thanks for your reply.
But, my fstab is already using the UUID.
So....

Any other suggestions?

Rgds
JIA

> **stee1rat said:**
> 2) I think you can add another line to /etc/fstab to mount your hard drives at startup.

---

