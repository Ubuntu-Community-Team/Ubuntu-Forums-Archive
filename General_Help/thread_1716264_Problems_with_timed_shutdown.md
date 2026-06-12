---
title: "Problems with timed shutdown?"
date: 2011-03-28
forum: General Help
---

### Post by TMacca on 2011-03-28
My PC using ubuntu 10.10 will not completely shutdown after a timed shutdown

e.g.      sudo shutdown +300

This is what comes up before everything halts and I have to forcefully shutdown the computer by holding in the power button

* Killing all remaining processes...
init: plymouth main process (27590) killed by KILL signali
init: rsyslog main process (995) killed by BUS signal            [fail]
init: rsyslog main process ended, respawning            
/etc/init.d/rc: 341: /etc/rc1.d/S90single: Input/output error
init: rsyslog main process ended, respawning
init: dbus main process (1055) killed by TERM signal
init: dbus main process ended, respawning
init: Disconnected from system bus
init: network-manager main process (1228) killed by BUS signal

please tell me how to fix this?

---

### Post by ~Plue on 2011-03-28
try with the 'h' switch
sudo shutdown -h +300

from man shutdown:
> 
-h     Halt or power off after shutdown.


---

### Post by TMacca on 2011-04-10
> try with the 'h' switch
sudo shutdown -h +300

thank you, I can't believe I didn't know that!

---

