---
title: "FATAL: Module fuse not found."
date: 2010-03-05
forum: General Help
---

### Post by sdv on 2010-03-05
Hi,
I installed FUSE using fuse-2.7.4.tar.gz; but now, when I type
'modprobe fuse' in a terminal, it gives me: FATAL: Module fuse not found.
I don't know what I can do to solve this.

---

### Post by gmargo on 2010-03-05
You should say what version of Ubuntu and what version of kernel (linux-image) you are using.

For the latest & greatest (Ubuntu 9.10 Karmic, kernel linux-image-2.6.31-19-generic), the kernel is configured to include FUSE instead of compiling it as a module.  In other words, FUSE is compiled into the kernel, so there is no need (and no way) to load the "fuse" module.

You can see this in the kernel configuration file:
```

$ grep FUSE_FS /boot/config-2.6.31-19-generic 
CONFIG_FUSE_FS=y

```A loadable module would have an "m" instead of the "y".  "y" means compiled in.

Also, there is no need for you to compile fuse-2.4.7.  Just install the **libfuse2** and **fuse-utils** packages.  They are probably already installed.

---

### Post by sdv on 2010-03-05
Thank you!!

---

### Post by prabhuvishnumurthy on 2011-02-13
It is interesting to see some new information about FUSE filesystem. Thank you for that. I am working on FUSE kernel module so I want to compile it whenever I make a change to it. Since it is a built in module. I think I have to compile it every time which I dont want. so, what I am thinking is, what if I remove builtin module facility and make it as loadable module so, if I do any change I can compile it, reload it, if any problem occurs, I can just remove it!! .
Is there any possibilities to do so?

---

### Post by prabhuvishnumurthy on 2011-02-13
I dont want to compile it with the kernel every time.. that's what I mean.

---

