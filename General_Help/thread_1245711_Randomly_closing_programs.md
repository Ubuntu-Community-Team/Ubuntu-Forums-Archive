---
title: "Randomly closing programs"
date: 2009-08-20
forum: General Help
---

### Post by jonohull on 2009-08-20
I finally blew away Windows on my desktop and put on Jaunty (I've had Ubuntu on my laptop for a while now). I had install problems that I fixed, and it's all good now, but some programs randomly close for no reason. I would be working in Firefox or something and it would just act like I had pressed ctrl+q. Sometimes it does it when I'm trying to open a program like DC++. It opens for a split second, then closes without me being able to do anything. It doesn't happen all the time, but enough to make it bothersome and impractical. Any ideas?

---

### Post by doas777 on 2009-08-20
when an app closes, open a terminal and enter:
```
sudo dmesg | tail
```
that will show the last 10 debug messages, hopefully including some useful informaiton about what crashed and why. post it and we can take a look.

also have you done a ram test on your pc?

---

### Post by jonohull on 2009-08-20
Here is what came up; I'm guessing the last line is the relevant one.

> [   24.583723] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   82.896290] ondemand governor failed, too long transition latency of HW, fallback to performance governor
[  142.327767] wlan0: authenticate with AP 00:1c:10:90:2a:f6
[  142.329390] wlan0: authenticated
[  142.329394] wlan0: associate with AP 00:1c:10:90:2a:f6
[  142.331636] wlan0: RX AssocResp from 00:1c:10:90:2a:f6 (capab=0x411 status=0 aid=1)
[  142.331640] wlan0: associated
[  142.333412] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  152.816006] wlan0: no IPv6 routers present
[  312.047249] linuxdcpp[3566]: segfault at 5 ip b794cbec sp b3cc30e0 error 4 in libgdk-x11-2.0.so.0.1600.1[b78fa000+89000]


I have not done a memory test lately. Also, as soon as installed it worked, then there were a hundred updates at once, and I think one was a kernel update, and it didn't work after that.

---

### Post by doas777 on 2009-08-20
> **jonohull said:**
> Here is what came up; I'm guessing the last line is the relevant one.

I have not done a memory test lately.
i wonder if reinstalling build-essential or your compiler would help. it looks like your compiler is crashing while trying to build.

---

### Post by P4man on 2009-08-21
> **jonohull said:**
> I have not done a memory test lately. Also, as soon as installed it worked, then there were a hundred updates at once, and I think one was a kernel update, and it didn't work after that.

Had the same one one machine with the 2.6.28 kernel. By selecting an older kernel in the grub menu, the problem went away. Its worth trying, as its pretty easy to do. Just press escape to get the grub boot menu, and pick an older kernel. If that does cure it, we can tell you how to make the change permanent.

---

### Post by jonohull on 2009-08-26
Using an older kernel didn't help.

> **doas777 said:**
> i wonder if reinstalling build-essential or your compiler would help. it looks like your compiler is crashing while trying to build.

What is the best way to do this? I've been using linux a while, but not enough to know what to do in a situation like this.

---

