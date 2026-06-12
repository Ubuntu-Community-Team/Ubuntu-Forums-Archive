---
title: "Multiple restarts needed to achieve good boot"
date: 2011-03-25
forum: General Help
---

### Post by wisolman on 2011-03-25
Ubuntu 10.04 boots properly at least 95% of the time, but occasionally it takes about 20 minutes to boot and then runs very slowly. Using System Monitor I see that my 2 processors are constantly alternating between 100% and around 5% usage when the system should be idle. I restart and I get the message "Failed to load OS." Another restart results in a normal boot time but it displays a split screen (about a fifth of the right side of the desktop is shown on the left side of the screen). Another restart results in the failed to load OS message again. Another restart boots up normally and the computer runs normally.

Has anyone else experienced this behavior? Does anyone know what is causing this? Could it be a hardware problem?

---

### Post by wisolman on 2013-03-04
I'm running 12.04.2 now and was still having the occasional slow boot problem until today. I fixed the problem by removing the (unused) internal PCI Modem from my machine. I was led to this fix by this warning message (which was repeated hundreds of times): "serial8250 too much work for irq18".

---

