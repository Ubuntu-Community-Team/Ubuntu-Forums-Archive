---
title: "Screensaver not working..."
date: 2009-10-20
forum: General Help
---

### Post by Ghost|BTFH on 2009-10-20
As someone who's experienced this frustration of this and after noting many posts across the Internet over it (as well as a bug report) I thought I would share my solution with everyone in here.  If there's a better location for this thread, please relocate it to the correct area mods (with my most sincere apologies).

Basically, the problem is that you set your screen saver to activate after x amount of time.  At x time, the screen dims, almost goes black and much like a college student fighting the crash of caffeine while studying for his exam the next day, snaps back to normal after a brief moment...only to do the same thing again after the next period of inactivity.

This issue seems to be linked to the fact that APM and ACPI are both active for some bloody unknown reason.

Now, unless you are using a computer system that predates civilization (2000) there's no need for APM as your system will most likely have ACPI (Check your BIOS to be sure).  If that's the case, turn off APM in your services (APMD is what you're looking for) and if for some unknown reason, you're actually using a graphical display on a pre-2k system, turn off the ACPI (ACPID) in your services instead.

I believe this should resolve the problem and make life great in Linuxland once more.

Cheers,
Ghost|BTFH

---

