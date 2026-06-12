---
title: "Several questions regarding Kernelupdate"
date: 2009-10-21
forum: General Help
---

### Post by Senecae on 2009-10-21
Hey guys..

i have some main questions about kernelupdate. So.. lets begin :)..

I have a embedded linux system with 256mb Ram.. Now after several tries, i havent managed it to update the kernel on it. Now my Question: Is it possible to make a kernel on a another system (with the same linux os) with "make && make modules_install" and then simply copy the created bzImage to the embedded linux system and boot?

Any help would be deeply appreciated!

Kind Regards,

---

### Post by hal10000 on 2009-10-21
I never did it, but i'm sure you can. But it's not the standard procedure to compile a kernel. I guess you can read about this in the README.txt that comes with your kernel source. Maybe you should search in some kernel-oriented forums to find more information about the concrete procedure.

---

