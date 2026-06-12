---
title: "How do i report this bug if it is a bug?"
date: 2010-12-07
forum: General Help
---

### Post by dwarder on 2010-12-07
dwarder@liza:~/fooo/foo2zjs$ system-config-printer
**** Incorrect IEEE 1284 Device ID: [u'drv:///hp/hpcups.drv/hp-laserjet_p1006.ppd', u'drv:///hpijs.drv/hp-laserjet_p1006-hpijs.ppd']
**** Actual ID is MFG:Hewlett-Packard;MDL:HP LaserJet P1006;
**** Please report a bug against the HPLIP component
Using foomatic:HP-LaserJet_P1006-foo2xqx.ppd (status: 0)
**** Incorrect IEEE 1284 Device ID: [u'drv:///hp/hpcups.drv/hp-laserjet_p1006.ppd', u'drv:///hpijs.drv/hp-laserjet_p1006-hpijs.ppd']
**** Actual ID is MFG:Hewlett-Packard;MDL:HP LaserJet P1006;
**** Please report a bug against the HPLIP component

also when i try to add pdd (in system-config-printer) to my printer i got this error
"There was an error during the CUPS operation: 'server-error-internal-error'."

my version: Ubuntu 10.04 LTS

---

### Post by dcstar on 2010-12-08
> **dwarder said:**
> 
.........
**** Please report a bug against the HPLIP component
.........

```
ubuntu-bug hplip
```

---

