---
title: "How do I kill a 'sh' zombie?"
date: 2010-12-10
forum: General Help
---

### Post by AKADAP on 2010-12-10
Sometimes I find a process named 'sh' running under my username with the status 'zombie' waiting channel 'do_exit' on my system. Its ID increments by 4 every time System Monitor updates its display.

Today, it was there immediately after booting The only thing I did after logging in is start the System Monitor

I can't kill it since its ID changes too fast.

I don't know how it gets started, but it bothers me since it is behavior I would expect from something that is trying to hide.

If I hover over its name, the tool tip contains 'sh'

Any idea how to track down its source?

---

### Post by kidders on 2010-12-12
Hi there,

> **AKADAP said:**
> I can't kill it since its ID changes too fast.Zombie processes can't be killed (ie they're already dead). There's no reason to *want* to kill one either, since they aren't doing anything, and don't consume any resources.

It's also worth noting that a process's PID can't change. What you're seeing is a series of different "sh" processes being spawned, executing & terminating. The easiest way to figure out what they're doing is to look at their parent. Next time you see one, examine the output of **ps auxf** (or any process tree) & see if its parent still exists. Often, that's enough to make an educated guess ... or at least figure out where to go next.

Whatever's happening is unlikely to be anything abnormal/unusual, but there's at least a *small* chance these "sh" processes are being left in a zombie state long enough for you to notice them because they're forking and/or terminating faster than expected (ie a bug of some kind in the parent process).

I hope that helps.

---

### Post by AKADAP on 2010-12-12
> **kidders said:**
> 

It's also worth noting that a process's PID can't change. What you're seeing is a series of different "sh" processes being spawned, executing & terminating. The easiest way to figure out what they're doing is to look at their parent. Next time you see one, examine the output of **ps auxf** (or any process tree) & see if its parent still exists. Often, that's enough to make an educated guess ... or at least figure out where to go next.

Whatever's happening is unlikely to be anything abnormal/unusual, but there's at least a *small* chance these "sh" processes are being left in a zombie state long enough for you to notice them because they're forking and/or terminating faster than expected (ie a bug of some kind in the parent process).

I hope that helps.

I can't believe that an endless stream of zombie 'sh' tasks is normal.
In any case it is not happening right now, so I can't run the test, but I've written down the command and will run it next time I see an infinite spawn of 'sh' zombies.

---

### Post by AKADAP on 2010-12-13
> **AKADAP said:**
> I can't believe that an endless stream of zombie 'sh' tasks is normal.
In any case it is not happening right now, so I can't run the test, but I've written down the command and will run it next time I see an infinite spawn of 'sh' zombies.

It is back today, and appears to be caused by the "Camera Monitor" panel applet
```

user    2654  0.1  0.4 291332 25340 ?        Sl   11:49   0:00              \_ /usr/bin/python /usr/bin/cameramonitor
user    2956  0.0  0.0      0     0 ?        Z    11:51   0:00              |   \_ [sh] <defunct>

```

I just killed the "Camera Monitor" applet, and the zombies went away.

---

