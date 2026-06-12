---
title: "IOWait eats 100% cpu after sleep"
date: 2010-09-11
forum: General Help
---

### Post by pingvinus on 2010-09-11
Hi, after 2-3 sleep/wakeup routine (about 2-3 days uptime) I found, that right after wakeup ubuntu starts reading hdd that causes 100% iowait cpu. And it lasts over 30 minutes, so I need to make reboot every time.

I've tried `iotop` & killing processes by `ps aux | grep D`. But none help.
Also I've added `noatime` at fstab, but it doesn't help much too.

---

