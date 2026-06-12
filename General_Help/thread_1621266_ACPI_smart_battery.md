---
title: "ACPI smart battery"
date: 2010-11-14
forum: General Help
---

### Post by nunrgguy on 2010-11-14
Hi
Just installed 10.10 on an old acer 1502lmi which has KT800 mb and a dodgy BIOS that Acer never fixed. This box always had problems under windows with audio dropouts and freezing - the workaround was to hack the registry etc to stop checking for the battery. Recently re-installed windows and had the usual dropouts and freezing and the solution to the problem on the internet is long gone.

Audio is fine under Ubuntu but periodically the box will still completely freeze - just a complete lockup, totally unresponsive. I've tried switching acpi completely off but this stops sound and wifi working as I believe the interrupts clash.

As far as I remember the problems were due to checking the battery so the questino is how do I leave smart acpi runnint and switch off smart battery?

Thanks

---

### Post by nunrgguy on 2010-11-15
Right,further report. I've run without battery in the machine, was still crashing, I know there were some issues with speed stepping on these so have been running at a fixed 800mhz. The machine has been up for hours but then crashed - doesn't seem  to be freezing now, just a reboot. No hard drive errors reported and a brand new hard drive. Nothing in the error logs. TYhe crash occurs at random, the most recent when pausing a virtualmachine in virtualbox.

Going to do a memtest tonight to see if that's the problem.

Any other ideas?

---

