---
title: "Screen blanker in command line only Ubuntu"
date: 2010-10-19
forum: General Help
---

### Post by DRobertR on 2010-10-19
Hi,

I have an installation of Maverick using command line only. It switches the monitor to standby after only about 5 minutes. Previous Ubuntu server and command line only versions do this too. Does anybody know where the setting is to change or disable this behavior? Perhaps something to do with ACPI?

Thanks,

Dave

---

### Post by chessnerd on 2010-10-19
Take a look at setterm -blank:

```
       -blank [0-60|force|poke] (virtual consoles only)
              Sets  the  interval  of  inactivity, in minutes, after which the
              screen will be automatically blanked (using APM  if  available).
              Without an argument, gets the blank status (returns which vt was
              blanked or zero for unblanked vt).

              The force option keeps screen blank even if a key is pressed.

              The poke option unblank the screen.
```
Maybe upping the number of minutes there will help.

---

### Post by DRobertR on 2010-10-19
Thanks much for that command, I wasn't aware of it. It didn't seem to help though. The screen goes blank after 10 minutes of inactivity. Not a serious problem, but sort of annoying when I get up for 11 minutes and come back. I found the file /etc/kbd/config with the setting BLANK_TIME=30 and BLANK_DPMS=off. I tried changing those settings around with no effect. There's a comment in this file that says most kernels default to 10 minutes, which is what's happening. It seems those settings are there but not being used, and the kernel is overriding them.

I'll keep researching and see what I can find.

Thanks

---

