---
title: "Is it possible to resume from suspend with a CRON job ?"
date: 2009-07-13
forum: General Help
---

### Post by Chareos on 2009-07-13
Hi guys,

I'm trying to setup an automated power management on a machine that has no BIOS option "power on at xx:xx o'clock".

My best guess here is to put system at sleep after some inactivity, but then I've no way to power it on automatically at 6 o'clock, for example.

My question:
is it possible to bring on the system with a cron job ?
requirements:
- any suspend mode which is fan-less is suitable
- pc must be able to get back on, at a specified time (cron job in my guess)


Thank you for any suggestion !

---

### Post by Rob_H on 2009-07-13
Afraid not. Cron (and other Linux processes) will not be running when the computer is suspended. Some kind of BIOS support is needed to power it up. If the BIOS has a "wake-up on LAN activity" option, you might be able to power it up via another computer on the network.

---

### Post by prshah on 2009-07-13
> **Chareos said:**
> 
- pc must be able to get back on, at a specified time
Thank you for any suggestion !

As already mentioned, cron will not do the job here.

However, you can use apmsleep; but I don't know whether or not it will work for you, given that you do not have the RTC (real time clock) wake up facility in the BIOS.

The manpage for apmsleep will give you the details, but here's a summary```
apmsleep +1:00 # wake up after one hour
apmsleep 23:23 # wake up at 11:23 PM
apmsleep 26:15 # "wrap around" the time to wake up at 2:15 AM

```

If apmsleep does not work for you, you may have to disable power management by BIOS.

Finally, if nothing else works, there's always the good old wake-up-on-modem-ring option; if your telephone system supports it, you can set a telephone alarm for 6:00 am (or whatever).

---

### Post by Chareos on 2009-07-13
apmsleep sounds very nice...
except jaunty says me that the kernel has no apm compiled in.

Now, why Canonical includes an utility which relies on a kernel feature not included is beyond my imagination...

any acpi alternative ?

---

### Post by prshah on 2009-07-14
> **Chareos said:**
> apmsleep sounds very nice...
except jaunty says me that the kernel has no apm compiled in.

Now, why Canonical includes an utility which relies on a kernel feature not included is beyond my imagination...

any acpi alternative ?

Canonical must have decided that since APM is not SMP safe, and is replaced by ACPI, it would be better not to include it by default in kernels that operate on multiprocessors. 

The ACPI aternative is rtcwake. Usage is similar to apmsleep; please see manpage for details though.

---

