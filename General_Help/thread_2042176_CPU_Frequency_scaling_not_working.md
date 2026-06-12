---
title: "CPU Frequency scaling not working"
date: 2012-08-14
forum: General Help
---

### Post by marmistrz on 2012-08-14
Hi,
My CPU is always running at 2700 Mhz, even though ondemand governor is on. I have AMD Athlon X3 processor.
What's stranger, even if I set other frequency (e.g. 800, 1500, 2100), the 2700 Mhz frequency is set instead. Any governor causes 2700 Mhz to be used.

On Debian Squeeze, there's no such problem
I'm using Ubuntu 11.04
Why is it malfunctioning?
Thanks in advance

---

### Post by dcstar on 2012-08-14
> **marmistrz said:**
> Hi,
My CPU is always running at 2700 Mhz, even though ondemand governor is on. I have AMD Athlon X3 processor.
What's stranger, even if I set other frequency (e.g. 800, 1500, 2100), the 2700 Mhz frequency is set instead. Any governor causes 2700 Mhz to be used.

On Debian Squeeze, there's no such problem
I'm using Ubuntu 11.04
Why is it malfunctioning?
Thanks in advance

Install the **powernowd** package.

---

### Post by marmistrz on 2012-08-14
> **dcstar said:**
> Install the **powernowd** package.

I installed powernowd and run
```
sudo powernowd -d
```
But the problem persists...
I needed to download the deb, as powernowd is not in natty repos.
edit: after restart it's fixed. Thanks!

---

### Post by dcstar on 2012-08-15
> **marmistrz said:**
> 
.......
edit: after restart it's fixed. Thanks!

Then MARK the thread!

---

