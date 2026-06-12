---
title: "Multiple users = slowness"
date: 2010-04-21
forum: General Help
---

### Post by atomicmoose on 2010-04-21
I recently loaded 9.10 on my HP 6910p laptop and things have been going great.

One small caveat is that when I am logged on to the machine at the same time that another profile is loaded, the machine crawls.

It does not appear that I am using all of the available memory:

```
moose@Joyce-Laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1010072     956440      53632          0      59252     427260
-/+ buffers/cache:     469928     540144
Swap:      2955920        960    2954960

```

Is there something I can tweak here to improve performance? I never had this problem on this machine before 9.10.

TIA
Moose

---

### Post by MooPi on 2010-04-21
If you could post your system monitor results when this occurs. System monitor or top in terminal or better yet htop in terminal.

---

### Post by atomicmoose on 2010-04-22
> **MooPi said:**
> If you could post your system monitor results when this occurs. System monitor or top in terminal or better yet htop in terminal.
It occurs any time more than one user is logged into the machine. Here is a SS of htop.

[IMG]http://img.photobucket.com/albums/v711/atomicmoose/Stuff/Screenshot-1.png[/IMG]

---

### Post by atomicmoose on 2010-04-28
bump

---

