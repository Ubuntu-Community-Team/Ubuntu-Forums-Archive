---
title: "How do i install glibc 2.9?"
date: 2009-12-31
forum: General Help
---

### Post by hexbase on 2009-12-31
Hi,

I need to install glibc 2.9 to compile a program. How do i do that?
Download source, compile and install?

Thanks

---

### Post by Leppie on 2009-12-31
what release have you got installed, jaunty?
jaunty should have it in the repository.

---

### Post by hexbase on 2009-12-31
I have Karmic, according to gnome-system-monitor.

---

### Post by Buuntu on 2009-12-31
Have you tried using the repository?
If not type this into the terminal:
```
sudo apt-get install glibc-2.10-1
```It's a newer version but I'm sure it's backwards compatible with whatever you are trying to do.
If you don't know what repositories are, (I don't mean to insult you if you do) this might clear things up: [https://help.ubuntu.com/community/Repositories](https://help.ubuntu.com/community/Repositories)

---

### Post by Leppie on 2009-12-31
i found the package on launchpad: [https://launchpad.net/ubuntu/karmic/i386/libc6/2.9-23ubuntu1](https://launchpad.net/ubuntu/karmic/i386/libc6/2.9-23ubuntu1)
and the development package is there as well: [https://launchpad.net/ubuntu/karmic/i386/libc6-dev/2.9-23ubuntu1](https://launchpad.net/ubuntu/karmic/i386/libc6-dev/2.9-23ubuntu1)

---

### Post by hexbase on 2009-12-31
Thanks, i have solved it.

---

### Post by Leppie on 2009-12-31
> **hexbase said:**
> Thanks, i have solved it.

how did you solve it?

---

