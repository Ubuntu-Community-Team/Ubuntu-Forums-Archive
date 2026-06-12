---
title: "Low performance issues - please help to check these processes"
date: 2010-06-17
forum: General Help
---

### Post by Zeemvel on 2010-06-17
Unlike ubuntu 9.10, I constantly have problems with Ubuntu 10.4, such as performance issues.

If I type top, I see this:

>   PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 1153 root      20   0 64652  53m  15m S    1  1.6   0:08.22 Xorg
  363 root      20   0 10592 5784 3468 S    0  0.2   0:13.52 plymouthd
 2563 me     20   0  2544 1248  924 R    0  0.0   0:00.08 top
    1 root      20   0  2804 1728 1220 S    0  0.1   0:00.56 init
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0
    4 root      20   0     0    0    0 S    0  0.0   0:00.05 ksoftirqd/0
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
    7 root      20   0     0    0    0 S    0  0.0   0:00.07 ksoftirqd/1
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2
   10 root      20   0     0    0    0 S    0  0.0   0:00.02 ksoftirqd/2
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3


What are all those "migration" processes doing there?

What are all those "watchdog" processes doing there?

Why is "plymouthd" usually at the top and often taking CPU percentages?

Is there anything unusual in the list?

Thanks.

---

### Post by dcstar on 2010-06-17
> **Zeemvel said:**
> 
.........
Why is "plymouthd" usually at the top and often taking CPU percentages?

Is there anything unusual in the list?

Thanks.

Everything except plymouthd is normal and of no concern.

Plymouth is the boot screen which should exit when you see the login screen, it obviously isn't and I would imagine that is the root cause of your problems as it is gobbling CPU resources.

You can kill the process manually, or remove the package or change your Grub setup and remove the "splash" boot option and see if that makes a difference.

---

### Post by Zeemvel on 2010-06-25
If I use Synaptic Package Manager to remove plymouth, then it wants to uninstall virtually every application on my system, as if everything depends on plymouth.

So how can I get rid of it?

---

