---
title: "WRONG system clock; RIGHT hardware clock. How do I get Ubuntu to use hardware clock?"
date: 2010-06-23
forum: General Help
---

### Post by zefew on 2010-06-23
'date' and 'hwclock --show' show big differences in time.  Hardware clock keeps the correct time, but 'date', the system clock, doesn't (often wrong in a matter of hours).  So I'm sure it is the problem of the kernel.

I'm tired of synching hardware clock with the system clock all the time.

How do I get Ubuntu to use the hardware clock instead of its own in the first place?

---

### Post by sgage on 2010-06-23
Can it be that the system thinks the hardware clock is set to UTC? Check your settings and see if that box is checked.

---

### Post by zefew on 2010-06-23
> **sgage said:**
> Can it be that the system thinks the hardware clock is set to UTC? Check your settings and see if that box is checked.

No. Even if I set the correct time for the system clock, it runs slower, which will become apparent after an hour. So I end up running '/sbin/hwclock --hctosys' periodically, which is kinda stupid. So what I want to do is for Kernel to use the hardware clock in the first place.

---

### Post by dcstar on 2010-06-24
> **zefew said:**
> No. Even if I set the correct time for the system clock, it runs slower, which will become apparent after an hour. So I end up running '/sbin/hwclock --hctosys' periodically, which is kinda stupid. So what I want to do is for Kernel to use the hardware clock in the first place.

```
cat /sys/devices/system/clocksource/clocksource0/*
```

My system shows:

```
tsc hpet acpi_pm 
tsc
```

If you do not have **hpet** enabled in your BIOS then perhaps you should enable it?

---

### Post by zefew on 2010-06-24
> **dcstar said:**
> ```
cat /sys/devices/system/clocksource/clocksource0/*
```

My system shows:

```
tsc hpet acpi_pm 
tsc
```

If you do not have **hpet** enabled in your BIOS then perhaps you should enable it?

Mine's:
```
$ cat /sys/devices/system/clocksource/clocksource0/*
hpet acpi_pm 
hpet
```

Haven't studied how I should interpret this yet, but at least hpet is there.

---

### Post by john newbuntu on 2010-06-25
Your current clock source seems to be hpet.  You could try using tsc.

If you are using grub2, make the following change in the file /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clocksource=tsc"

If you are using grub legacy, add the last phrase to the kernel line in menu.lst.

Then run:
sudo update-grub

The other thing to try to rename "clocksource" to "clock" (although I think clock is deprecated in the later kernels).  Then repeat by running sudo update-grub and rebooting.

Note: You could also add these at boot time if you are familiar with editing the kernel command line.  If none of these work, revert it back to the original files and run "sudo update-grub" and you are back to square one.

---

### Post by zefew on 2010-06-25
> **john newbuntu said:**
> Your current clock source seems to be hpet.  You could try using tsc.

If you are using grub2, make the following change in the file /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash clocksource=tsc"


John,

Thanks for your suggestion. Certainly I've never seen anyone mentioning changing
the clocksource before, which is a nice surprise.  I tried it, but after a
reboot, the system became incredibly slower somehow. It felt as if it were using
only 1/2 cpu power. So I reverted it. Same result on another reboot. So I
decided to revert the change.  I didn't try it with "clock" though, since the
kernel on my system is 2.6.31-14-generic, which should be considered relatively
newer.

---

### Post by john newbuntu on 2010-06-25
To me it appears that the clocksource is trying to losing some clock interrupts and ends up losing time when it shouldn't.  Sorry I was not of much help there, although I would suggest you to try the clock=tsc or clock=pmtmr option.  Read these:
[http://ubuntuforums.org/showthread.php?t=956263](http://ubuntuforums.org/showthread.php?t=956263)
[http://ubuntuforums.org/showthread.php?t=614226](http://ubuntuforums.org/showthread.php?t=614226)

If you search of clock drift or slow/fast on google, you will find a number of such suggestions, mostly involving kernel parameters.  I do not know about your system info and kernel.  But hopefully some of these fixes should help.

---

### Post by dcstar on 2010-06-25
> **john newbuntu said:**
> Your current clock source seems to be hpet.  You could try using tsc.
..........

**NO!** the first line of that output is **available** clock sources, the second is the actual clock source used.

You cannot select a clock source that does not exist.

---

### Post by john newbuntu on 2010-06-25
@dc: Do you know if the list of available clocksources be extended to include tsc perhaps by a BIOS change/flash or are we stuck with hpet and acpi_pm?  If so, that would solve this issue.  hpet, I understand is slow.  I was hoping introducing a kernel parameter would attempt it to use a different clocksource and hence the tsc based gettimeofday().  Could there be a module missing?  I know mine and yours use tsc and I am happy with my clock times(no significant drifting).
Is ntpd another option to keep things in sync?

@zefew: What version of kernel and OS are you using?  I was trying to suggest using a different kernel to see if it helps.

---

### Post by zefew on 2010-06-26
John,

Thanks a bunch for pointing me to the right direction.  I tried several
approaches suggested in one of the links in #8 and found that appending "noapic
nolapic" option worked like a charm :)

I now have only 3 sec drift in 1 hour on average (where "drift" is calculated
from pool.ntp.org's time), which I would assume is not deviant. 

To answer what you asked in your previous post:

  kernel = 2.6.31-14-generic
  os = ubuntu karmic

Thanks again.

---

### Post by zefew on 2010-06-26
By the way, "noapic nolapic" shouldn't cause a performance problem since my computer has Atom processor, which is single-core. 

Disadvantage of noapic nolapic - Ubuntu Forums  [http://ubuntuforums.org/showthread.php?t=3000](http://ubuntuforums.org/showthread.php?t=3000)

Advanced Programmable Interrupt Controller  [http://osdev.berlios.de/pic.html](http://osdev.berlios.de/pic.html)

---

