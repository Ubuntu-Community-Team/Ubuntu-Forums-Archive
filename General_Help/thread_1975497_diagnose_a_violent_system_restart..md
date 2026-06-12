---
title: "diagnose a violent system restart."
date: 2012-05-07
forum: General Help
---

### Post by javaholic on 2012-05-07
My system has just recently starting experience some violent system restarts.  How would you go about trying to diagnose where the fault is?

The only explanation of this violent restart that i can give is that i'm experiencing a power outage with the caveat the system immediately restarts from the BIOS onwards without fault.

This has made the system really unstable and unreliable to the extent i can't do any worthwhile productive work on it for risk of losing it.

So far i have only ruled out the external HDD and mountall.

There is nothing i can do to prevent this from happening once system decides it wants to restart.

What would be your first port of call in determining what is at the root of the problem?

As i type this there is something that up to now i hadn't considered.  It might be a bad memory module.  How would i ascertain this?

---

### Post by 2F4U on 2012-05-07
The first thing that I would do is look through the log files in /var/log. The second thing I would do if restarts come out of the wild is
- verify that the temperature doesn't get too high
- check the RAM by running memtest from a liveCD

---

