---
title: "lm-sensors not detecting new AMD 945 Quad-Core in Hardy"
date: 2009-10-05
forum: General Help
---

### Post by charonred on 2009-10-05
I'm using Hardy 8.04.3 LTS and have been running lm-sensors since about Sept last year with my AMD 2.8Ghz Athlon Dual-Core without a problem.

Today I upgraded the CPU to a  new AMD 3.0Ghz Phenom 945 Quad-Core (just released 95w version), but it only shows 2 cores in sensors-applet 2.2.1 (which keeps popping up an error message when trying to update reading)

Also I'm using SysmonitorScreenlets v0.1 and where it used to display graphs for each of the dual-cores, it now only displays a '**AMD Processor model unknown**'.

All 4 cores show in Ubuntu's System Monitor 2.22.3; so how do I get the sensors/graphs working properly again? or do I need some other applet/screenlet?

---

### Post by trstncmpbll on 2009-10-06
im pretty sure that applet only shows cpu0 and cpu1. there has to be a way to change that though

---

### Post by charonred on 2009-10-06
thanks; and I'm also thinking it may be because the 945 is a relatively new model, and the 95 watt version I got has only just been released and hit the stores here yesterday; so I might have a wait till whatever 'libraries' are updated.

I also noticed that 'AMD Processor model unknown' is displayed on booting PC, so I might need a new BIOS update; currently I have F6 which is required for this 945 CPU, but there is also a F7 available ... might have to look into that as well.

---

### Post by trstncmpbll on 2009-10-06
that could be it. i know some people that have the same problem that couldnt solve it (or are too lazy) but im pretty sure it can be done, id be curious to know what you find out

---

### Post by dcstar on 2009-10-06
> **charonred said:**
> thanks; and I'm also thinking it may be because the 945 is a relatively new model, and the 95 watt version I got has only just been released and hit the stores here yesterday; so I might have a wait till whatever 'libraries' are updated.

I also noticed that 'AMD Processor model unknown' is displayed on booting PC, so I might need a new BIOS update; currently I have F6 which is required for this 945 CPU, but there is also a F7 available ... might have to look into that as well.

Apart from updating the BIOS, you may well have to use more modern kernel & sensors packages that recognises the later CPU.

You may be able to fetch and install both from the 9.10 repository at:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by charonred on 2009-10-06
I'll download new BIOS later.

PC is currently running 2.25.24-23 kernel, as 2.6.24.24 introduced a non-silent splash screen ... lots of text instead of background colour, so I don't use that one. But I'll have a look at 9.10's kernel, as long as I can run that and not have to install 9.10 itself ... tried alpha's of 9.10, but they have problems with ATI and dual monitors (same as 9.04 Jaunty did).

I use the PC for business, so 8.04.3 LTS is better for me

---

### Post by charonred on 2009-10-06
> Apart from updating the BIOS, you may well have to use more modern kernel & sensors packages that recognises the later CPU.

You may be able to fetch and install both from the 9.10 repository at:

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

went there, but don't know exactly what I should be looking for or which section to look in ?

---

### Post by charonred on 2009-10-06
I've just updated BIOS from F6 to F7, and it now identifies the CPU as AMD Phenom(tm) II X4 945 - great ... but

Sysmonitor still won't display CPU graphs; if I 'tick' the View CPUs box it displays 3 CPUs - 2 at top as normal, but 1 at bottom, and looses all other info.

---

### Post by charonred on 2009-10-06
installed another Screenlet 'AllCoreCPUUsages' as well; so I don't have 'View CPUs' enabled in Sysmonitor (just all other data), and have a new separate screenlet that displays activity graph of all 4 cores.

Still have problem with lm-sensors though; it continues to display CPU fan speed, front & rear case fan speeds, system temp & Northbridge temp; but not the CPU core temps.

---

