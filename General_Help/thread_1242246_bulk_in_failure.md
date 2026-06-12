---
title: "bulk in failure"
date: 2009-08-16
forum: General Help
---

### Post by dupaski on 2009-08-16
I'm getting tons of these messages have no idea what they mean:

* "kernel: [39220.395987] Bulk In Failed. Status=-71, BIIdx=0x5, BIRIdx=0x5, actual_length= 0x0"*

I'm running Jaunty x64 on a dell server and everything seems to be working well, but from the logs it seems that something isn't working just right. Looking up "Bulk In Failed" on the net dosen't tell a newbie like me what the issue is. What exactly is bulk in and what should I be woried about breaking if it keeps failing?

Derek

---

### Post by Wulfrunner on 2010-06-03
You can find a description of the problem and its solution here:
[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/373680)

It's NetworkManager's roaming gone horribly wrong.

---

