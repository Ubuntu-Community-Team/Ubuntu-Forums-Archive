---
title: "random shutdowns on my server."
date: 2010-07-23
forum: General Help
---

### Post by niiklas on 2010-07-23
My server has the last couple of days had 3-4 random shutdowns. Where can i find the reason? which logs etc. Im pretty sure its not power failure since my other devices hasnt lost power.. alarm clocks etc.

I appreciate any help :)

---

### Post by nemilar on 2010-07-23
You can look in /var/log/messages

Here is my 8.04 machine rebooting:

```
Jul  8 00:56:43 orion -- MARK --
Jul  8 01:10:46 orion syslogd 1.5.0#1ubuntu1: restart.
Jul  8 01:10:47 orion kernel: Inspecting /boot/System.map-2.6.24-28-generic
Jul  8 01:10:47 orion kernel: Loaded 27937 symbols from /boot/System.map-2.6.24-28-generic.
Jul  8 01:10:47 orion kernel: Symbols match kernel version 2.6.24.
Jul  8 01:10:47 orion kernel: Loaded 15535 symbols from 77 modules.
Jul  8 01:10:47 orion kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  8 01:10:47 orion kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  8 01:10:47 orion kernel: [    0.000000] Linux version 2.6.24-28-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu May 27 00:16:49 UTC 2010 (Ubuntu 2.6.24-28.70-generic)

```

You may also want to look at /var/log/syslog

---

### Post by niiklas on 2010-07-23
Didnt find anything out of the ordinary in those logs. just a bunch of marks that ended at 13:40~. I noticed i had some temperature problems, cleaned and remounted the cooler. Maybe my problems are gone now.. :)

[IMG]http://lasias.com/download/nhogblom/cpukylare.png[/IMG]

> **nemilar said:**
> You can look in /var/log/messages

Here is my 8.04 machine rebooting:

```
Jul  8 00:56:43 orion -- MARK --
Jul  8 01:10:46 orion syslogd 1.5.0#1ubuntu1: restart.
Jul  8 01:10:47 orion kernel: Inspecting /boot/System.map-2.6.24-28-generic
Jul  8 01:10:47 orion kernel: Loaded 27937 symbols from /boot/System.map-2.6.24-28-generic.
Jul  8 01:10:47 orion kernel: Symbols match kernel version 2.6.24.
Jul  8 01:10:47 orion kernel: Loaded 15535 symbols from 77 modules.
Jul  8 01:10:47 orion kernel: [    0.000000] Initializing cgroup subsys cpuset
Jul  8 01:10:47 orion kernel: [    0.000000] Initializing cgroup subsys cpu
Jul  8 01:10:47 orion kernel: [    0.000000] Linux version 2.6.24-28-generic (buildd@rothera) (gcc version 4.2.4 (Ubuntu 4.2.4-1ubuntu3)) #1 SMP Thu May 27 00:16:49 UTC 2010 (Ubuntu 2.6.24-28.70-generic)

```

You may also want to look at /var/log/syslog

---

### Post by nemilar on 2010-07-23
Nice picture ;)

Hope cleaning that off helps your problems.

---

### Post by niiklas on 2010-07-31
> **nemilar said:**
> Nice picture ;)

Hope cleaning that off helps your problems.

yeah it did :) thanks for your help :)

---

