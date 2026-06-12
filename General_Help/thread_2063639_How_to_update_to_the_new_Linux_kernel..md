---
title: "How to update to the new Linux kernel."
date: 2012-09-27
forum: General Help
---

### Post by linuxvstheworld on 2012-09-27
I heard about the newly patched Linux kernel and I was wondering how to update to it via Ubuntu 12.04. Is it possible?

---

### Post by snowpine on 2012-09-27
Beginner method: Upgrade to each new Ubuntu release as it becomes available. (12.10 next month, 13.04 next April, etc.) This guarantees you are always using the latest kernel, applications, desktop environment, etc.

Intermediate method: Add [Ubuntu mainline kernel PPA]("http://askubuntu.com/questions/47397/how-do-i-add-the-kernel-ppa") to your software sources.

Advanced method: Download source code for the latest kernel from [kernel.org]("http://kernel.org") and [compile it yourself]("https://help.ubuntu.com/community/Kernel/Compile").

---

### Post by linuxvstheworld on 2012-09-27
So when new Ubuntu versions come out they should have the latest Linux kernel?

---

### Post by snowpine on 2012-09-27
Each Ubuntu release uses a recent stable kernel as of the date of its release. 12.10 will have a 3.5 kernel, I believe.

---

### Post by snowpine on 2012-09-27
Also at the risk of stating the obvious (apologies if this comes of as insulting but I don't know your level of Linux knowledge) 99% of Linux users do not want/need the latest kernel all the time. I only ever consider a kernel upgrade if I'm having a specific hardware or performance problem that I know can be remedied with a specific newer kernel.

---

### Post by linuxvstheworld on 2012-09-28
> **snowpine said:**
> Also at the risk of stating the obvious (apologies if this comes of as insulting but I don't know your level of Linux knowledge) 99% of Linux users do not want/need the latest kernel all the time. I only ever consider a kernel upgrade if I'm having a specific hardware or performance problem that I know can be remedied with a specific newer kernel.

Oh ok.
I'm fine with my Ubuntu laptop anyways, I just wanted to know if Ubuntu will stay up to date with the kernel. Thanks!

---

### Post by Louisraritan on 2012-09-28
Asked the same question when I had Karmic.  The problem you run into with adding a new kernel to an old stable release is that it can break your applications.  Learned the hard way to just wait for the next stable version of Ubuntu for the newest kernel.  If you just like to tinker and learn, try virtual box and Arch Linux.

---

### Post by d4m1r on 2012-09-28
Kernel updates will be picked up by "Software Updater" automatically and you will be prompt whether or not to upgrade to them automatically.

---

