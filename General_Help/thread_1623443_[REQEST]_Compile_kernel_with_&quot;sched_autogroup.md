---
title: "[REQEST]: Compile kernel with &quot;sched_autogroup_enabled&quot; patch"
date: 2010-11-16
forum: General Help
---

### Post by odejoy on 2010-11-16
Has anyone tried compiling a custom kernel (from git source), with the "[[COLOR="Blue"]sched_autogroup_enabled[/COLOR]]("http://marc.info/?l=linux-kernel&m=128978361700898&w=2")" patch on the current (fully updated) maverick meerkat?

If so, will the brave soul please share their experience and how they did it.

The reason I am interested in it is due to the fantastic [[COLOR="Blue"]desktop responsiveness[/COLOR]]("http://www.phoronix.com/scan.php?page=article&item=linux_2637_video") gains.

Thanks!

---

### Post by snek on 2010-11-18
I am also **really **interested in this patch!
Hope someone manages to create a stable generic x64 kernel with this ;)

---

### Post by pdoes on 2010-11-20
Done :) Not in a x64 environment, but i386.

```
# cat /proc/sys/kernel/sched_autogroup_enabled 
1
# uname -a
Linux MonteCarlo 2.6.35-23-tty #40-Ubuntu SMP Fri Nov 19 22:58:39 EST 2010 i686 GNU/Linux

```

I'll write up an article on how I did it this weekend. During patching some of the hunks failed and one file is in a different directory as apposed to 2.6.37. I'll offer the new patch on my site as well.

Does it work? I have no idea, I haven't done any comparison with the old setup.

---

### Post by pdoes on 2010-11-22
Here's the article on how to compile a Ubuntu 10.10 kernel with "sched: automated per tty task groups" kernel patch

[http://blog.avirtualhome.com/2010/11/22/how-to-compile-a-ubuntu-10-10-maverick-kernel-with-sched-automated-per-tty-task-groups-kernel-patch/](http://blog.avirtualhome.com/2010/11/22/how-to-compile-a-ubuntu-10-10-maverick-kernel-with-sched-automated-per-tty-task-groups-kernel-patch/)

---

### Post by rdtripp on 2010-11-24
> **pdoes said:**
> Here's the article on how to compile a Ubuntu 10.10 kernel with "sched: automated per tty task groups" kernel patch

[http://blog.avirtualhome.com/2010/11/22/how-to-compile-a-ubuntu-10-10-maverick-kernel-with-sched-automated-per-tty-task-groups-kernel-patch/](http://blog.avirtualhome.com/2010/11/22/how-to-compile-a-ubuntu-10-10-maverick-kernel-with-sched-automated-per-tty-task-groups-kernel-patch/)

There is a typo in your article.

skipabi=true skipmodule=true fakeroot debian/rules binary-core2

should be

skipabi=true skipmodule=true fakeroot debian/rules binary-tty

---

### Post by pdoes on 2010-11-24
I fixed the article.

---

