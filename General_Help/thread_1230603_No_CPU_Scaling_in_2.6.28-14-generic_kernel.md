---
title: "No CPU Scaling in 2.6.28-14-generic kernel?"
date: 2009-08-03
forum: General Help
---

### Post by Epidural on 2009-08-03
I'm running 64-bit Jaunty on an Intel Core2Duo E8400, and according to the Gnome taskbar plugin "CPU Frequency Scaling Moniter", my CPU no longer scales either of the cores of the CPU. Normally at idle, 2.00GHz is the output of the plugin, however now it is constantly at 3.00GHz (100%) for both cores. This happened directly after the restart when updating to the latest kernel via the update manager (kernel 2.6.28-14-generic according to the "uname -a" output.)

Anybody else having the same problem? If so, did you fix it? If not, should I file a bug report?

PS: The cpu activity meter from the System Moniter plugin reports accurately, and shows 0% - 1% usage during idle periods. Normally, the CPU scaling would not increase from 2.00GHz on either core until around 40%+ CPU usage was used, sometimes even longer. As well, the temperature of the CPU is remaining as it would if the CPU was working at a lower frequency (around 44'C). Does this mean the applet is at fault? Is there a command-line output that would tell me my current CPU frequency as well?

EDIT: The    'cat /proc/cpuinfo'    command showed my a command-line text of the current CPU frequency, and it conquers with the "3003.000MHz" (3.00GHz) that the plugin states.

EDIT/HALF-ASSED SOLUTION: Just tried turning the "SpeedStep" option in the BIOS to "Enabled" instead of "Auto". This seems to have fixed the problem, hopefully it will not cause compatibility issues. It seems Jaunty lost its own ability to scale the CPU? I'm guessing that the CPU itself is now throttling, and not the OS as was possibly the case before. Also, I think 45'C must have been the norm when my room was warmer, for the CPU temp is now hovering at around 38'C at idle.

Anybody else having this issue can try as I did, with a BIOS setting. But if the new kernel was the problem, I'd appreciate anybody else with this issue commenting on this thread (so I know it's not just my specific case), as it would help to file a bug report.

---

