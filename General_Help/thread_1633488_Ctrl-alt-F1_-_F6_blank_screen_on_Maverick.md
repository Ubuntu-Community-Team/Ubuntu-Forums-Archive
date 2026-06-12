---
title: "Ctrl-alt-F1 - F6 blank screen on Maverick"
date: 2010-11-29
forum: General Help
---

### Post by _Duhhh on 2010-11-29
I recently installed Maverick 64-bit on a new HP 8740w (NVidia Quadro FX 2800M video). When I try to open a console using CTRL-ALT-F1, I get a blank screen (no cursor). The console is running (I can log-in blind), but no video. I have tried several solutions (modifying the GRUB video mode, and the solution in [this]("http://ubuntuforums.org/showthread.php?t=999550") thread. Nothing changed. I am using NVidia driver v173. WHen I revert to "current" I get a console login, but gdm won't start.

Any suggestions to get both gdm and console at the same time? I'm trying to configure the system so I can use multi-monitor in a docking station, so I'd like to know I can get to a visible console before I try that.

I should mention that I was able to see the console just after installing 10.10, but in the days since, something (update?) changed to cause it to go blank. I had to make a few changes to get ACPI to behave on this system. I'm not sure when the console went dark.

---

### Post by _Duhhh on 2010-12-18
Latest beta NVidia driver solved this issue (and several other video issues).

---

