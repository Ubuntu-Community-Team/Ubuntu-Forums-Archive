---
title: "System clock randomly stops"
date: 2009-07-31
forum: General Help
---

### Post by Spanglegluppet on 2009-07-31
Occasionally, I will come back to the computer to find my system clock is an hour or two behind. (as in, it's still going, but stopped for a little while along the way)

I'm using Ubuntu 8.10 on an Acer Aspire 5610 laptop.

Any solutions?

---

### Post by Arup on 2009-07-31
Change your motherboard battery.

---

### Post by Spanglegluppet on 2009-07-31
> **Arup said:**
> Change your motherboard battery.

Think that's the problem? I do need a new battery, as the one I have is very old and provides possibly about 10 minutes of battery life (no exaggeration.) I'll try it, thanks.

---

### Post by sedawk on 2009-07-31
Is it always exactly one hour or two hours?

If my knowledge is up-to-date, the system clock of linux is
only synced with the hardware clock when you boot your PC.
While linux is running it doesn't bother about the hardware clock
anymore, it uses "CPU ticks" to calculate a more exact time without
caring about the hardware clock anymore.
[Although that might have changed with the latest generations of
 power saving CPUs ...]

In a terminal you can run "date" to view the system time and
you can run "hwclock --show" to check the clock on your motherboard.

If your clock is always behind an hour or two I suspect a problem
with time synchronization and time zones.
(But even if you use something like ntp it should refuse to do corrections
 that are that big.).

If the clock goes wrong a few minutes then you might have an issue
with the system clock timing or you have to configure the apic
kernel parameter.

---

### Post by aesis05401 on 2009-07-31
@Spanglegluppet - so a reboot fixes this?  There are reports of issues with system clocks losing up to a few minutes a day, but I only know of this happening on Alpha hardware.  Please let us know what hardware you are using.  

@sedawk - One important thing to highlight from your post: system clock = kernel time, so discrepancies should be met with raised eyebrows.  System clock is set by the hardware clock on boot, but the hardware clock is recalibrated to the system clock on shutdown.

Normal time loss happens like this:
(First Boot)
Hardware clock is calibrated during installation
User chooses timezone & local or UTC timekeeping

(Every Boot)
OS boots & system time is set from hardware clock
System time precision is much higher than hardware time, so after a long uptime the two clocks are different, sometimes by a lot.
System receives shutdown command, and the high precision kernel time (system clock) is used to recalibrate the low precision hardware clock. 

If the recalibration on shutdown does not happen because of crash or hang on shutdown, then the next boot will see the system clock set to the wrong time by the hardware clock - but it is only fractions of time on properly functioning/modern hardware so most users never see a large impact.. 

If the system clock is actually losing relative time - for example your computer time matches yur watch when you turn it on, but a few hours later it no longer matches the time on your watch - this is a kernel problem.  

A cmos battery dying would explain the first type of time loss because it would take only one incomplete shutdown to get a wacky time from the hardware clock on next boot.  A cmos battery would not explain the second type of loss.

Does this help?

---

