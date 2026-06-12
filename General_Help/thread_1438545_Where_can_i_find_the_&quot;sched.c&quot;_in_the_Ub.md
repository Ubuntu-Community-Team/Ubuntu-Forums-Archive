---
title: "Where can i find the &quot;sched.c&quot; in the Ubuntu 9.10"
date: 2010-03-25
forum: General Help
---

### Post by harish4linux on 2010-03-25
Dear all Members,

Please help me where can i find the scheduler source core "sched.c" file inside ubuntu 9.10 file system

I need to study the scheduler functionality for my project purpose

please help me as soon as possible......

---

### Post by gmargo on 2010-03-25
To install the linux source code for the kernel that you are running (assuming 9.10 Karmic):
```

sudo aptitude -V -R install linux-source
cd $HOME
tar xjfv /usr/src/linux-source-2.6.31.tar.bz2
cd linux-source-2.6.31
cd kernel
ls -l sched*

```

Or get the source with "apt-get source" like this:
```

apt-get source linux-image-2.6.31-20-generic

```

Or you can go straight to the source.  Here's Linus' kernel tree: [http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=summary](http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=summary) with instructions on getting a copy here: [http://git.kernel.org/](http://git.kernel.org/).  Linus' kernel download weighs in at about 365MB. "sched.c" and other "sched_*.c" files reside in the kernel/ subdirectory. (Click the "raw" link to see the file contents.)

---

