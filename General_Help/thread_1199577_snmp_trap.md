---
title: "snmp trap"
date: 2009-06-29
forum: General Help
---

### Post by b-boy on 2009-06-29
Hi guys I need help generating a snmp trap

---

### Post by Soul-Sing on 2009-06-29
Something like: snmptrapfmt ?
Or nagios?

---

### Post by The Cog on 2009-06-29
There is an SNMP trap generating utility in the snmp package.
**sudo aptitude install snmp**
The utility is called snmptrap. You will need to consult these two man pages:
man snmptrap
man snmpcmd

Since it is a command line utility, you can put the trap generation in a script that you run whenever appropriate.

---

