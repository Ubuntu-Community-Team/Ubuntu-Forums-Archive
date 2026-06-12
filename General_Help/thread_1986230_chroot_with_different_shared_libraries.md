---
title: "chroot with different shared libraries?"
date: 2012-05-24
forum: General Help
---

### Post by Cowloon on 2012-05-24
Hi,

Is it possible to have separate shared libraries in a chroot environment than without? So far, I've only seen mention of how to copy shared libraries that a program needs into the environment.

I want to create a chroot environment and build shared libraries that are different than the non-chroot environment, e.g. whizbang-pro version x in non-chroot and whizbang-pro version y in chroot environment.

My laptop is too slow for virtual machines to be usable. It's disk is too small for dual-boot. And, I'd like to avoid figuring out how to make a lot of programs statically linked.

Oh yeah: If it is possible, do I just make a separate copy of ld.so.conf?

---

### Post by Cowloon on 2012-05-27
I tried it. Yes, it works.

---

