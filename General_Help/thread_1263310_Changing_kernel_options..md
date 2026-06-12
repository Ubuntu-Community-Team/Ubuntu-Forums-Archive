---
title: "Changing kernel options?."
date: 2009-09-10
forum: General Help
---

### Post by sunrex on 2009-09-10
I need to change a few options in my kernel:

> 
Processor type and features:
Disable Tickless System (Dynamic Ticks)
Enable High Resolution Timer Support
Select your processor under Processor family
Change Preemtion Mode to Complete Preemption (Real-Time)
Enable Enable priority boosting of RCU read-side critical sections (ignore if not present)
Disable Enable tracing for RCU - currently stats in debugfs (ignore if not present)
Enable Machine Check Exception and select Intel or AMD depending on your CPU
Change Timer frequency to 1000 HZ
Power management options
Enable Power Management support
Disable Power Management Debug Support
Disable Suspend to RAM and standby
Disable Hibernation (aka 'suspend to disk')
Enable ACPI (Advanced Configuration and Power Interface) Support
Disable CPU Frequency scaling
Disable CPU idle PM support
Networking
Networking options
Enable Packet socket: mmapped IO
Optionally disable Network packet filtering framework (Netfilter) (Warning: this will disable your firewall!)
Disable QoS and/or fair queueing (Unless you need and use it...)
Device Drivers
Disable Watchdog Timer Support
Enable Real Time Clock
Enable PC-style 'CMOS'
Kernel hacking
Disable everything


Any idea on how I can do this without screwing everything up?. Thank you.

---

### Post by Whiffle on 2009-09-10
That'll be a kernel compile.  Although alot of that list is pretty vague...

[https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html](https://help.ubuntu.com/6.10/ubuntu/installation-guide/i386/kernel-baking.html)

Just make sure you don't remove the old kernel and you will always be able to reboot into the old kernel.

---

