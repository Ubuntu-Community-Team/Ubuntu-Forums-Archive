---
title: "Linux Kernel Panic"
date: 2012-06-11
forum: General Help
---

### Post by Revolutionary101 on 2012-06-11
Today I experienced something that I have never seen before: a Linux kernel panic. Now I know as much as anyone that no OS is perfect. OSs are made by humans and humans make mistakes so no OS is going to be perfectly stable and bug free. Even so some OSs come close (Linux anybody?). Anyways I was wondering what causes a kernel panic and possibly how I can prevent it from happening in the future. Thank you!

---

### Post by sabinedoll on 2012-06-18
Hello,

I am not an expert. I also experienced a whole lot of kernel panics after an update to a new kernel version, every time I tried to log in.

As In am unable to fix the problem, I am running Ubuntu with an older kernel version, which is stable and does not have any problems.
(when restarting the computer, select "previous linux versions" and choose one of the previous kernels)

Hope this helps until the real bug is fixed.

---

### Post by Redblade20XX on 2012-06-18
> **Revolutionary101 said:**
> Today I experienced something that I have never seen before: a Linux kernel panic. Now I know as much as anyone that no OS is perfect. OSs are made by humans and humans make mistakes so no OS is going to be perfectly stable and bug free. Even so some OSs come close (Linux anybody?). Anyways I was wondering what causes a kernel panic and possibly how I can prevent it from happening in the future. Thank you!

Anything in essence can cause a kernel panic (ie. hardware and/or software faults). The kernel is just the bridge between the hardware and software and vice versa. If a memory location become corrupt hardware wise, this may trigger a kernel panic when the OS tries to allocate something to that location. On the other hand, poorly written code (such which causes tremendous memory leaks) can also cause a kernel panic.

-Red

---

