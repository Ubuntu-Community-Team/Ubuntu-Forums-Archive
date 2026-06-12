---
title: "120 megs of programs in use, 1.4gigs total mem consumption"
date: 2010-01-14
forum: General Help
---

### Post by rene197705 on 2010-01-14
Generally i like ubuntu, but i find this problem puzzling;

i've got < 200 megs of mem consumed by programs in use (sys monitor), but total mem consumption is at 1.4gigs
and no way to see what subsystem is the pig.

i'm gonna give gentoo a try.

---

### Post by Richard1979 on 2010-01-14
Could just be cache mem.
You can verify this by opening a Terminal and typing "top". (q to quit)

Could also be a tmpfs (ramdisk) mount somewhere, you can type "mount" and see if anything like "tmpfs" or "/dev/shm" is in the list.
If you think you don't need this then you can comment this out in /etc/fstab with a # symbol by running "sudo nano /etc/fstab" then use CTRL + O then CTRL + X to save changes.

---

### Post by CrimsonBizarre on 2010-01-14
Linux does that. The memory isn't actually using that much.

As soon as another program needs that memory - it will give it to the program. Rather than wasting all that memory. It shouldn't slow your computer.

---

### Post by Hallvor on 2010-01-14
> **rene197705 said:**
> Generally i like ubuntu, but i find this problem puzzling;

i've got < 200 megs of mem consumed by programs in use (sys monitor), but total mem consumption is at 1.4gigs
and no way to see what subsystem is the pig.

i'm gonna give gentoo a try.

If 200 MB is consumed by applications in use - that sounds normal. The 1,4 GB you are describing is probably just cache that will be freed if your applications need the RAM.

What is the point of RAM if you never use it?

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

---

### Post by running_rabbit07 on 2010-01-14
Please do not forget to mark the thread [solved] once you are happy.:)

---

