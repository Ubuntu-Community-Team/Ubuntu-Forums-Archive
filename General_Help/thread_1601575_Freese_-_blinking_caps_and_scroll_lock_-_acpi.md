---
title: "Freese - blinking caps and scroll lock - acpi"
date: 2010-10-20
forum: General Help
---

### Post by SriNarayanan on 2010-10-20
Sony Vaio EB 16 FG - running ubuntu 10.10 froze while resuming from dimmed screen with blinking scroll lock and caps log LED.

The scenario was this :-
I just downloaded the acpi using synaptic package manager.
Then installed laptop mode tool using synaptic.

*cat* /proc/sys/vm/laptop_mode
0

Means its not yet enabled.

But decided to remove it .(read  drive spin up and down is not good for HDD)

Had left the laptop for some time , it dimmed screen . When I resumed it froze.
No mouse movement.only blinking caps and scroll.

Just wondering if acpi is the culprit,since haven't seen this behaviour before and it happened after removing  laptop mode tools

---

### Post by SriNarayanan on 2010-10-20
It happened again , this time while playing a movie on totum .
I was running top on another terminal just to see cpu usage .

Now remove acpi , let me see if it happens again after the removal.

---

### Post by SriNarayanan on 2010-10-22
just today had another kernel panic , also just now came to know that this system behaviour is called kernel panic

see if this help

[http://ubuntuforums.org/showthread.php?t=1603231](http://ubuntuforums.org/showthread.php?t=1603231)

---

### Post by SriNarayanan on 2010-10-24
> **SriNarayanan said:**
> just today had another kernel panic , also just now came to know that this system behaviour is called kernel panic

see if this help

[http://ubuntuforums.org/showthread.php?t=1603231](http://ubuntuforums.org/showthread.php?t=1603231)


it happened again while on youtube

---

### Post by SriNarayanan on 2010-10-24
Somebody shed some light on this . its more trouble ..Going to remove ubuntu and put open suse :-(

---

