---
title: "What on earth is polkit doing ?????"
date: 2012-03-18
forum: General Help
---

### Post by Jethro_uk on 2012-03-18
I leave my machine on 24/7, and connect in via X2Go. Logging in last week, I noticed that memory usage, out of 4Gb was running at 95% - the machine was doing absolutely nothing. Digging through the processes, it seemed "polkitd" was using nearly 3Gb of memory.

I killed the process, and immediately, memory usage dropped to about 3%.

Logging in again today, guess what ? Yup ... memory usage was at 97%, and it was polkitd again.

Can anyone tell me (a) if this is expected and (b) what on earth polkitd does to need that much memory.

After all, if I wanted weird processes to start using all my resources, I would have stuck with windows.

---

### Post by TeoBigusGeekus on 2012-03-18
[Seems to be a bug]("https://bugs.launchpad.net/ubuntu/+source/policykit-1/+bug/572813").

---

### Post by Helen McCall on 2012-03-18
You have discovered a long standing bug in polkitd

see [http://ubuntuforums.org/showthread.php?t=1450707&highlight=polkitd](http://ubuntuforums.org/showthread.php?t=1450707&highlight=polkitd)

---

