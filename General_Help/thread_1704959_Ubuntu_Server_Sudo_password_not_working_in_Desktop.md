---
title: "Ubuntu Server Sudo password not working in Desktop Environment"
date: 2011-03-11
forum: General Help
---

### Post by GazMathias on 2011-03-11
Hi,

I have installed ubuntu-desktop and can log in fine. Whenever I start Synaptic, etc and am prompted for my password I am told it is incorrect.

I reinstalled ubuntu server and tried the same thing with xubuntu-desktop and I experience the same thing.

Am I missing something?

---

### Post by krishna1650 on 2011-03-11
> **GazMathias said:**
> Hi,

I have installed ubuntu-desktop and can log in fine. Whenever I start Synaptic, etc and am prompted for my password I am told it is incorrect.

I reinstalled ubuntu server and tried the same thing with xubuntu-desktop and I experience the same thing.

Am I missing something?

Use command "gksu-properties" and select authentication mode as "sudo". This should solve the problem.

---

