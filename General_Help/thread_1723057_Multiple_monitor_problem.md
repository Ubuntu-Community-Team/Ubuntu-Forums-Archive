---
title: "Multiple monitor problem"
date: 2011-04-06
forum: General Help
---

### Post by t0p on 2011-04-06
I recently set up my desktop computer (Pentium 4 processor, nvidia grahics card, running Lucid) on a new desk, and I decided I'd like a 2-monitor set-up.  I've got a few CRT monitors kicking around, and I've tried different monitors in different configurations, but I keep having the same problem: the monitor connected to the main VGA socket works okay, but a secong monitor connected to the extra VGA output on the back of the computer will not work - it just goes into energy-saving mode (ie. the green light turns orange).

I've installed grandr on the computer, so I have menu **System > Preferences > Monitors** and **System > Administration > Multiple Screens** but neither tool allows the computer to see the extra monitor.

Strange thing is, if I unplug the second monitor it displays the NO SIGNAL display.  So, the second monitor obviously knows it's connected to a computer - but it won't actually work.

Any ideas why this is happening/how to fix it?  Cheers.

---

### Post by TeoBigusGeekus on 2011-04-06
If you're using nvidia's restricted drivers, try to do the configuration with nvidia's tools
```
gksu nvidia-settings
```

---

### Post by t0p on 2011-04-06
> **TeoBigusGeekus said:**
> If you're using nvidia's restricted drivers, try to do the configuration with nvidia's tools
```
gksu nvidia-settings
```

I'm not using nvidia's restricted drivers.

```

t0p@phobos:~$ which nvidia-settings
t0p@phobos:~$ 

```

```

t0p@phobos:~$ gksu nvidia-settings
t0p@phobos:~$ 

```

---

