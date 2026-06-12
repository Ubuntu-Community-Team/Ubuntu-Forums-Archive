---
title: "Ubuntu freezes after disuse"
date: 2011-12-03
forum: General Help
---

### Post by Rsjc741 on 2011-12-03
I tend to keep my computer on during the day for reference, etc.

I had the same problem when I started out installing Mac OSX:

The screen would shut off, as normal, then the computer would hit some unrecoverable error and freeze. Leaving the screen on still caused the installer/OS to crash.

I've also had this problem for as long as I could remember for this machine.

Its fairly recent.. it's coming up on its first "build-day", with a much needed expansion from 4 to 16 GB of RAM.

Here's the specs to anyone who thinks it might be helpful:

Mobo: MSI H55M-E33
CPU: Intel i5 760 @ 2.8~2.95 GHz
RAM: 4GB DDR3
Graphics Card: PNY Nvidia GTX 560 Ti
Boots: Ubuntu 11.10, Windows 8

One note.. I can't remember if this helped at all, but I think once I switched RTC Wakeup event from BIOS to OS, it helped the problem.

However, the freezes happen in Ubuntu -- and the settings on OS.

This is extremely annoying and possibly destructive to my files and my hard drive. Any suggestions are welcomed.

My guess is that theirs a hardware/software issues.. most likely my WMP300N communicating via NDISwrapper with the OS. It's been buggy from day 1.


Update:

I'm seeing if making C3 the idle state for ACPI, instead of C1, will make the freeze stop happening.
Anyone know anything about Intel/C-states in general incompatibility?

---

