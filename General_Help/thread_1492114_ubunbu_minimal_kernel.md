---
title: "ubunbu minimal kernel"
date: 2010-05-24
forum: General Help
---

### Post by xinxinren on 2010-05-24
I am a newbie and I am using ubunbu minimal 9.10 now, but I would need to add a driver. I was told that the driver is already in the kernel code, I would need to enable it and to recompile the kernel. I would like to ask two questions, please help.

1. if I would use kernel .config file from ubuntu minimal 9.10's, then I should be able to build a kernel that is exactly the same is the one I get in ubuntu minimal 9.10's kernel (I remember that the kernel version is 2.6.32), is it right?
2. if I would use the new built kernel, then I should get the same performance, such as bootup, as the ubuntu 9.10 minimal. 

I should be able to reproduce the kernel, but I would like to make sure that I will get what I want. Thanks in advance.

Regards

---

### Post by kerry_s on 2010-05-24
> 
I was told that the driver is already in the kernel code, I would need to enable it and to recompile the kernel


if its in the kernel, then all you have to do is modprobe it to turn it on, there should be no need to compile anything.

tell us what driver your looking for & as much info as you know.

---

### Post by xinxinren on 2010-05-24
kerry_s,

nice to hear you again. I would need r6040 network driver.

Regards

---

