---
title: "limiting bandwidth"
date: 2010-01-06
forum: General Help
---

### Post by hyburn on 2010-01-06
hey folks,

lets face it linux rocks.... we own the bandwidth,

my question is: is it possible to reduce my own bandwidth use?

teach me how to write a script to limit my bandwidth please

---

### Post by chewearn on 2010-01-07
When you said "bandwidth", are you referring to limit on transfer rate, or limit on total transfer amount?

---

### Post by sliketymo on 2010-01-07
> **hyburn said:**
> hey folks,

lets face it linux rocks.... we own the bandwidth,

my question is: is it possible to reduce my own bandwidth use?

teach me how to write a script to limit my bandwidth please

Stop watching so much pron,and you-tubes would be a good start.

---

### Post by Lars Noodén on 2010-01-08
If you are viewing the same pages often, then squid can help by caching them locally.  That's probably the most likely way to reduce bandwidth usage.

---

### Post by bodhi.zazen on 2010-01-08
I was going to suggest adblock (block unnecessary images) + a caching proxy.

Squid is a bit heavy, Polipo is an alternate.

You can also use privoxy, as most apps, such as firefox, cache pages anyways (unless you configure them not to).

A proxy cache makes sense with more then one user and more then one Deskto on a LAN, IMO, otherwise privoxy is fine.

iso images and multimedia use much more bandwidth then text.

---

### Post by Lars Noodén on 2010-01-08
> **bodhi.zazen said:**
> ... Polipo ... otherwise privoxy ...

Thanks.  Those look useful.

---

### Post by bodhi.zazen on 2010-01-08
> **Lars Noodén said:**
> Thanks.  Those look useful.

You are most welcome. Nothing wrong with squid mind you, nice to have some alternatives sometimes.

---

### Post by hyburn on 2010-01-09
how do I install squid? is the command:
"sudo appt-get install squid"?

FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
CPU Usage: 0.000 seconds = 0.000 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted
FATAL: Could not determine fully qualified hostname.  Please set 'visible_hostname'

Squid Cache (Version 2.6.STABLE18): Terminated abnormally.
CPU Usage: 0.000 seconds = 0.000 user + 0.000 sys
Maximum Resident Size: 0 KB
Page faults with physical i/o: 0
Aborted

---

### Post by Lars Noodén on 2010-01-09
> **hyburn said:**
> ...
FATAL: Could not determine fully qualified hostname.  **Please set 'visible_hostname'**
...

Check the configuration file for setting a host name or set something in DNS if you have access.  Some applications allow use of /etc/hosts, if I recall correctly, squid is one of them.

---

