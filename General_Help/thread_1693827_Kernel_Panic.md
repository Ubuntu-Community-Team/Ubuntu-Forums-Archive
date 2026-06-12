---
title: "Kernel Panic"
date: 2011-02-23
forum: General Help
---

### Post by Tych on 2011-02-23
Hi there,

I'm currently trying to get Ubuntu running on my Desktop PC but ist always freezes with a Kernel Panic.
I tried Ubuntu 10.04 and 10.10 both as 32Bit and 64Bit version, the latest Knoppix and Damn Small Linux. They all freeze with a Kernel Panic on startup (startup sound runs in a loop and numlock blinks endlessly)  running as Live CD.
Also tried to install the mentioned distributions but with the same freezing problem.
Finally, I found an old CD with Ubuntu 8.10 and managed to install it. It's possible to boot this version but after 30-60 sec running the kernel panic appears again.

I am relatively new to Linux. So can please someone tell me how to find out what could cause the kernel panic. (Already checked my RAM)

My system is:
Mainboard: Asrock P55 Deluxe
Graphics: Nvidia GTX 470
RAM: 6GB
CPU: Intel i5 750

---

### Post by epud on 2011-02-23
Hi Tych

I am also having a kernel problem. Here is the thread I started about it: [http://ubuntuforums.org/showthread.php?t=1693860]("http://ubuntuforums.org/showthread.php?t=1693860")

What kernel problem do you have. Is it similar?

---

### Post by An Sanct on 2011-02-23
Tych: could you please post the contents of the kernel log? You can find it throug System > Administration > Log File Viewer, named something like "kern.log" or "kern.log.1" or, from terminal in this directory:
```
/var/log/kern.log
```

---

