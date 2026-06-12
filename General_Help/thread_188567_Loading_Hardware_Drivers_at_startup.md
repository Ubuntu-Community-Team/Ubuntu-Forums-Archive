---
title: "Loading Hardware Drivers at startup"
date: 2006-06-04
forum: General Help
---

### Post by BjoeHrn on 2006-06-04
Hey!
At first of all sorry for my english, it's not so well.

I've a little problem with my Ubuntu computer. From time to time, it hangs up at startup while it try to excute "Loading Hardware Drivers".
Last boot I get a fail while "Loading Hardware Drivers". But I can't find anything in the log files.

Can anybody help me? It would be very nice!

Some information about my system:
CPU: AMD Athlon(tm) 64 Processor 2800+ (1889.948 Mhz) CPU-Cache: 512 KB
But I use the 32bit version.

Regards
Bjoern

---

### Post by givré on 2006-06-04
[QUOTE=BjoeHrn]
Last boot I get a fail while "Loading Hardware Drivers". But I can't find anything in the log files.
[/QUOTE]
Which log file did you watch at, you should try /var/log/syslog to know more about your problem

---

### Post by BjoeHrn on 2006-06-04
I watch into the messages and syslog, too.
But I dind't find something like the "Loading Hardware Drivers"-Fail :-/... I see nothing that bread a fault like this.

Here are my log files:
[http://www.bjoern-ribniger.cc/logs/](http://www.bjoern-ribniger.cc/logs/)

Bjoern

---

### Post by givré on 2006-06-04
I can't access your file man (403 Forbidden)
Did you try to run in recovery mode to have more information about your problem.

---

### Post by BjoeHrn on 2006-06-04
Sorry, now you can access my log files.
No, I didn't try in recover mode.

---

### Post by givré on 2006-06-04
As you, i can't see anything wrong in your logs. Is it working correctly anyway. I f it is, i think you just have to ignore these (false?) error.
But have a look at whats happens in recovery mode to be sure.

---

### Post by codypumper on 2006-06-04
If it makes you feel better, I've had the same problem yet all my hardware functions properly. I'm not comlain though, 'cause I already had a xserver problem and had to make a fresh install of dapper.

---

### Post by Szekely on 2006-06-05
Hello, I'm sort of having the same problem as BjoeHrn, except Ubuntu won't start at all. It just hangs on Loading Hardware Drivers.  I'm using the latest 6.06 version, tried a reinstall, all to no avail.  I'm hoping someone here can help me with my problem.

---

### Post by givré on 2006-06-05
Boot in recovery mode and see where there is a problem. Post there the errors and we will be abaible to help you

EDIT: but you should post your problem on a new thread, this one is not appropiate(not the same problem), and you will be able to have a better audiance

---

