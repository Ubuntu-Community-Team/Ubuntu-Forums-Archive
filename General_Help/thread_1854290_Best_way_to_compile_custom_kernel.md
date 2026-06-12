---
title: "Best way to compile custom kernel?"
date: 2011-10-04
forum: General Help
---

### Post by ojdon on 2011-10-04
Hi there, I'm looking to create a custom kernel for my Lubuntu 11.04 install but kernel.org is still down so I can't use KernelCheck. Is there a tutorial for the way to do it currently while kernel.org is down?

---

### Post by ojdon on 2011-10-04
Anyone?

---

### Post by spiky001 on 2011-10-04
Looks like kernel.org is up again

---

### Post by ojdon on 2011-10-04
Damn, KernelCheck is throwing a 404 error, though.

---

### Post by spiky001 on 2011-10-04
will this help [http://www.linuxforums.org/articles/the-newbies-guide-to-compiling-your-first-kernel_272.html](http://www.linuxforums.org/articles/the-newbies-guide-to-compiling-your-first-kernel_272.html)

---

### Post by ojdon on 2011-10-05
Not at the moment, I don't think. None of the kernel sources appear to be available just yet from kernel.org.

---

### Post by WorMzy on 2011-10-05
You get get the source code from [github]("https://github.com/torvalds/linux/"). You can clone the git tree, or just download the packaged source code from [here]("https://github.com/torvalds/linux/downloads").

---

### Post by dino99 on 2011-10-05
[https://git.kernel.org/?](https://git.kernel.org/?)
[https://github.com/torvalds/linux](https://github.com/torvalds/linux)

---

### Post by Lars Noodén on 2011-10-05
When you compile your kernel, make it into a package for APT.  That way it is easy to install/uninstall it.

---

### Post by ojdon on 2011-10-05
Ah thanks for the alternate links.

---

