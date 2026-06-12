---
title: "Kubuntu 11.10 Freezes"
date: 2011-12-01
forum: General Help
---

### Post by gus_zernial on 2011-12-01
I have a system with Gigabyte GA-990XA-UD3 mobo, Phenom II X6 and Radeon HD 5750 graphics card, running Kubuntu 11.10, 3.1.2-030102-generic kernel and fglrx from the repositories (not the Catalyst drivers downloaded from ATI).

The system is not stable and freezes (hangs) intermittently, plus both chromium-browser and thunderbird crash frequently. When the system freezes I can't get a console using ctrl-alt-Fn, and when chromium-browser and thunderbird crash I get dmesg output like:

chromium-browser ......
chromium-browse[2565]: segfault at 68e88968 ip 00007f0463be2c08 sp 00007fff2dd58e50 error 4 in libX11.so.6.3.0[7f0463bad000+133000]

Thunderbird ......
Inconsistency detected by ld.so: ../sysdeps/x86_64/dl-machine.h: 466: elf_machine_rela_relative: Assertion `((reloc->r_info) & 0xffffffff) == 8' failed!

I'm not at a level that I understand what these messages mean, or how to track down the problem. And when the system freezes I can't get to the console even to read the logs.

I note that this system has been upgraded over time from 10.04 to 11.04 to 11.10, and at one time it had the ATI Catalyst drivers, which I've hopefully completely removed, as they gave me much heartburn. I wouldn't be surprised if this is still an fglrx-related problem ... or some inconsistency issue with all the packages (and thus libraries) I've installed over time.

So my question is ... what can I do to further diagnose and/or fix the problem.

Thx, Gus

---

