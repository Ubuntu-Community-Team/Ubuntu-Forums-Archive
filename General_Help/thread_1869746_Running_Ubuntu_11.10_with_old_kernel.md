---
title: "Running Ubuntu 11.10 with old kernel"
date: 2011-10-26
forum: General Help
---

### Post by XMAG on 2011-10-26
Hello,

As a few people may know, a bug was introduced to the linux kernel somewhere between version 2.6.35 (Ubuntu 10.10) and 2.6.38 (Ubuntu 11.04) that made ANY linux distro prohibitively slow on some laptops including my ASUS N51.

At the time I could not find a solution so I abandoned linux and waited for a new generation of Ubuntu or Fedora to see if the bug would go away. It was not the case and Ubuntu 11.10 still runs slow as hell on my laptop, to the point I can't even install it in less then 12 hours or boot the LiveCD in less than an hour.

I contacted a few people with similar hardware and at this point I am pretty sure it is an incompatibility issue at the kernel level.

**So I was wondering if it is possible to install Ubuntu 11.10 with the 2.6.35 Linux Kernel, and if so how can I do it.**

Installing with 3.x kernel and then downgrading will eventually work but I would guess it will take me almost a week for the whole process to finish so I'm looking for a way of teaking the 11.10 distro to include kernel 2.6.35 from the start... Is it possible? And if so can anyone explain me how?

Thank you!

Caio

---

### Post by linuxwin2 on 2011-10-26
It's possible.
You can install kernel package and modify your grub to boot on this old kernel
[http://thanhsiang.org/faqing/node/129]("http://thanhsiang.org/faqing/node/129")

---

