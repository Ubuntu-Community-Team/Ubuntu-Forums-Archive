---
title: "System locking up with tons of hard drive activity"
date: 2011-01-31
forum: General Help
---

### Post by Raugturi on 2011-01-31
I am running Ubuntu 11.04 64-bit on my work laptop and at least a few times a day the entire system crashes.  When it happens my hard drive activities goes completely insane and the system is totally unresponsive.  The only way I am able to get out of it is to manually power the machine off, which I worry is going to cause other problems if I have to keep doing it.  Everything important is backed up, but restoring from scratch is a headache even so.

My main question is, how can I find out what the culprit is?  There doesn't seem to be any one thing I can do to always make it crash, but it does happen more often when I have a lot of things open at once, which makes me wonder if it's not something to do with memory caching.

Update: After correcting the UUID in /etc/fstab and in /etc/initramfs-tools/conf.d/resume everything seems to be fine.  I started everything I could think of to waste memory and while it did obviously slow down, it remained responsive enough to use the active application and to close everything back out without powering down manually.

---

### Post by McNils on 2011-01-31
I think that your computer starts to swap. The computer is unusable when it start to run out of memory. How much memory and swap do you have?

Have a system monitor running or a terminal with top. It should give you a clue.

---

### Post by Raugturi on 2011-01-31
Well I think I've figured out the cause...

```
$ swapon -s
Filename				Type		Size	Used	Priority
$ swapon -a
swapon: cannot find the device for UUID=056a858e-926d-489b-9f51-927f974a6703
```

Now I have to figure out where my swap went.

---

### Post by Raugturi on 2011-01-31
So apparently when I added a new partition it changed the UUID of swap.  I have now updated it in /etc/fstab and /etc/initramfs-tools/conf.d/resume.  Is there anywhere else I would need to manually update it?

---

