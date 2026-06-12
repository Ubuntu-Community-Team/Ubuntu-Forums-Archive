---
title: "ld linking to the wrong libGL.so"
date: 2010-05-07
forum: General Help
---

### Post by Alex Flint on 2010-05-07
Hi there,

I've recently upgraded from karmic to lucid and am having problems linking to libGL.so. It seems that ld links to /usr/lib/libGL.so.177.80, which is in conflict with the kernel module (which is 195.36.15).

ldconfig reports the following:
```
	libGL.so.1 (libc6,x86-64) => /usr/lib/nvidia-current/libGL.so.1
	libGL.so.1 (libc6,x86-64) => /usr/lib/libGL.so.1
	libGL.so.1 (libc6) => /usr/lib32/nvidia-current/libGL.so.1
	libGL.so.1 (libc6) => /usr/lib32/libGL.so.1
```

Why are there two identical entries for libGL.so?

/usr/lib/libGL.so.1 is a symlink to /usr/lib/libGL.so.177.80, whereas I think it should point to /usr/lib/nvidia-current/libGL.so.1. Why is this? I've run ldconfig to try to update the links but no effect. Why is /usr/lib/libGL.so.177.80 even present?

---

### Post by dino99 on 2010-05-07
i suppose you are not using the lucid genuine repo

---

### Post by Alex Flint on 2010-05-17
> **dino99 said:**
> i suppose you are not using the lucid genuine repo

Should I be? How? Which nvidia drivers would that use?

---

