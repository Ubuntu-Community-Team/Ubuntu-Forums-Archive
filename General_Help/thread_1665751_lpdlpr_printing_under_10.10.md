---
title: "lpd/lpr printing under 10.10"
date: 2011-01-12
forum: General Help
---

### Post by jbrandv on 2011-01-12
I just upgraded from 10.04 to 10.10 and my print server for other Unix/Linux systems is broken. I've tried cups-bsd, lprng, lpd, etc. But no joy. A RedHat 5.2 that used to print fine now reports: 
Network host 'xxxxx' is busy; will retry in 30 seconds
Another Redhat 5.0 reports: Network host 'xxxxxx' is busy, down, or unreachable
What happened to LPD support?  How do I get this working again?:confused:

---

### Post by jbrandv on 2011-01-12
Solved!  xinetd was borked during the upgrade. I removed it completely and reinstalled.  Working like a camp again.:KS

---

