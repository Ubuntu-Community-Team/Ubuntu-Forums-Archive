---
title: "Don't continue startup while disks are beeing checked"
date: 2010-03-10
forum: General Help
---

### Post by AllesMeins on 2010-03-10
Since 9.10 ubuntu continues to boot while the regularly disk checks are running and completes them in the background. For me this leads to a lot of problems, becasue i've some applications that depend on the other disks. So they fail to start if the disk in question is still being checked.
Simple question: How can I restore the old behavior - the startup process should be suspended until the disk checks are completed?

---

### Post by dcstar on 2010-03-11
> **AllesMeins said:**
> Since 9.10 ubuntu continues to boot while the regularly disk checks are running and completes them in the background. For me this leads to a lot of problems, becasue i've some applications that depend on the other disks. So they fail to start if the disk in question is still being checked.
Simple question: How can I restore the old behavior - the startup process should be suspended until the disk checks are completed?

[https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/439604](https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/439604)

---

### Post by AllesMeins on 2010-03-12
So this was designed being well aware of the possible consequences for users with more than one hard disk. And nobody felt the need to really warn users about that? Well thanks for wasting my time! That was just unnecessary and stupid!

Anyway - thanks for the help, dcstar.

---

