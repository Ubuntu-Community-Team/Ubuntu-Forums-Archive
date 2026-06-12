---
title: "Left computer on overnight, frozen by morning..."
date: 2009-07-22
forum: General Help
---

### Post by SEMW on 2009-07-22
Last night, I left the computer on overnight to run a backup.

When I came back to it this morning, it was completely frozen -- Ctrl-Alt-Backspace / Ctrl-Alt-F* had no effect.  The system clock still read 3:14 AM.

Alt-Sysreq-REISUB worked, and after rebooting, I went through all the logs in the system log viewer.  Nothing had any entries past 3:05; the last (logged) things to happen before the freeze were two cron jobs, one at 3:00 and one at 3:05, both lasting for under 5 seconds.  The backup had aborted for unrelated (trivial) reasons before 2 o'clock.

Anyone had anything like this happen before?

Running 9.04.

---

### Post by sarfarazkazi on 2009-07-22
Maybe your system got too hot and triggered auto shutdown. Worth checking the cpu & mobo temperatures.

---

### Post by SEMW on 2009-07-22
> **sarfarazkazi said:**
> Maybe your system got too hot and triggered auto shutdown. Worth checking the cpu & mobo temperatures.
My CPU temperature generally stays at about 40°C; it certainly shouldn't have been much above that whilst doing nothing whatsoever at 3AM.  Also, by BIOS is set to warn me (i.e. beep) when the temperature reaches 80; something that definitely would have woken me up.

I've 'stress-tested' the CPU (i.e. played games) on it quite a few times, and it's never even reached the alarm temperature, let alone tried to shut down.  I don't think it can be that.

Thanks, though!

---

### Post by ubiedubie on 2009-07-22
I have experienced this issue on 9.04 on my laptop.

The issue was the NVidia 180 drivers, I reverted back to the older ones (173 I think) and there were no more problems :KS

I hope that is the problem because its easy to fix!

---

### Post by SEMW on 2009-07-22
> **ubiedubie said:**
> The issue was the NVidia 180 drivers, I reverted back to the older ones (173 I think) and there were no more problems :KS
I hope that is the problem because its easy to fix!

I'm afraid I have an ATi card and am using the default open source "radeon" driver.

Thanks though!

---

