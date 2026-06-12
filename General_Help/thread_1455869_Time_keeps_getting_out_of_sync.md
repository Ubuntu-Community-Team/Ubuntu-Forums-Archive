---
title: "Time keeps getting out of sync"
date: 2010-04-16
forum: General Help
---

### Post by paulsp on 2010-04-16
Hi everyone,

I have Ubuntu 9.10 installed on a computer that does NOT have an internet connection. The time keeps getting out of sync, though. In one day it gets behind some 6 hours or so. And that keeps getting more and more. Reading through forums I found solutions but these do not apply. Please note:

[LIST]
[*]This is not a dual boot system. The system only runs Ubuntu.
[*]The CPU is not overclocked.
[*]The BIOS time is OK (set to GMT).
[*]The timezone is OK (set with dpkg-reconfigure tzdata)
[/LIST]
I have another computer which has the same problem (same PC, both bought recently with Ubuntu installed on them). There I was able to solve it using the auto-sync option. But this is not an option for the other PC as it does not have an internet connection. Any other ideas?

Regards,
Paul

---

### Post by dcstar on 2010-04-17
> **paulsp said:**
> Hi everyone,

I have Ubuntu 9.10 installed on a computer that does NOT have an internet connection. The time keeps getting out of sync, though. In one day it gets behind some 6 hours or so. And that keeps getting more and more. Reading through forums I found solutions but these do not apply. Please note:

[LIST]
[*]This is not a dual boot system. The system only runs Ubuntu.
[*]The CPU is not overclocked.
[*]The BIOS time is OK (set to GMT).
[*]The timezone is OK (set with dpkg-reconfigure tzdata)
[/LIST]
I have another computer which has the same problem (same PC, both bought recently with Ubuntu installed on them). There I was able to solve it using the auto-sync option. But this is not an option for the other PC as it does not have an internet connection. Any other ideas?

Regards,
Paul

```
man hwclock
```

---

### Post by paulsp on 2010-04-17
Thanks, I will check it out. Also, I found a BIOS setting for energy saving which supposedly possibly affects the clock in my computer model. So we will see if this works...

---

### Post by happyhamster on 2010-04-17
Another thing you could look into is which clocksource is used by your system, and if there are others available.

- In a terminal:

dmesg | grep clock -i

- should give some general info, while:

cat /sys/devices/system/clocksource/clocksource0/current_clocksource

- should show which clocksource is being used. And:

cat /sys/devices/system/clocksource/clocksource0/available_clocksource

- should show all clocksources available. To test a different clocksource, boot into the grub menu, highlight the kernel you want to boot and press "e". Then search for a line (it will be spread out over multiple lines):

linux /boot/vmlinuz......................................quiet splash

- And add:

clocksource=tsc

- or clocksource=hpet , or etc. (choose one that is available for you). Press Ctrl-x to boot. Next, check if the new clocksource is being used, and if the clock behaves any better.

Note: this is a pretty safe procedure, because all will be back to normal after a reboot. Only when you're *sure* everything works fine, should you consider making that change permanent by editing grub.

Good luck, and keep us informed.

---

### Post by paulsp on 2010-04-17
Wow, there is quite some settings behind something you'd say is as simple as the date and time of the computer! Let me check if this is fixed, and if it isn't I will try these things. Thanks a lot for the information!

---

