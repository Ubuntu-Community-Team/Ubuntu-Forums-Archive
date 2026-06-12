---
title: "turning off performance counters"
date: 2009-12-04
forum: General Help
---

### Post by shawnisalk on 2009-12-04
I'm not sure if this is the right forum for this question. Pardon me, if I've erred.

Here's the issue:

X wouldn't boot this morning on my Karmic system.
At the end of the boot process was this message:

vboxdrv: Warning: 2.6.31+ kernel detected. Most likely the hardware performance
vboxdrv: counter framework which can generate NMIs is active. You have to prevent
vboxdrv: the usage of hardware performance counters by echo 2 > /proc/sys/kernel/perf_counter_paranoid

After the message was a terminal login prompt and I was able to login just fine.

I edited perf_counter_paranoid and the only entry there is: 2
Just for kicks, I switched this to: 1
But that reset itself to: 2 when I rebooted.

I am running Virtual Box with a WinXP system inside, and although I don't use it often, I did use it immediately prior to shutting down my system last night. I'm wondering if Vbox didn't competely shutdown before I shut off the computer and it booted with some settings that are set when it's turned on intact.

Anyway, anyone have any suggestions? 

Thanks,
Shawn

---

### Post by shawnisalk on 2009-12-04
Nevermind. Solved my own problem.

When trying to "startx", it produced this error:

"Error locking authority file /home/shawn/.Xauthority"

I deleted this and recreated an empty version and this solved the problem.

---

