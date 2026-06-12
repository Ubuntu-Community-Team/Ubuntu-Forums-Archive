---
title: "Lost Disk Space"
date: 2011-03-02
forum: General Help
---

### Post by gavoby on 2011-03-02
I have installed ubuntu on 160 of the space on my laptop. Now I cant access the other space that is on it. How can I get to it?

---

### Post by jerome1232 on 2011-03-02
Let me get this right.

I'm assuming that you had a laptop with

Windows installed on it
and 160 GB of unallocated space (not being used by Windows).

You installed Ubuntu to that 160 GB of unallocated space, leaving the partition Windows is on alone.

You now want to access the partition that Windows is on from Ubuntu.


is that correct?

also
What is the output of this command from a terminal. (it will list all your drives and their partitions.)

```
sudo fdisk -l
```

---

### Post by gavoby on 2011-03-02
Hi There,

Yes and thanks, that helped. :)

---

