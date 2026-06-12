---
title: "ntop usage!!"
date: 2009-07-23
forum: General Help
---

### Post by harivittal.hk on 2009-07-23
hi!! when i gave sudo ntop , this is what i got on terminal...
the snapshot of it is here..
but i want to knw  my b/w usage currently and of this month till date..
how to knw tat using ntop,has it got any options..plz help..:)
Thursday 23 July 2009 01:32:01 PM IST  Now running as requested user 'nobody' (65534:65534)
Thursday 23 July 2009 01:32:01 PM IST  Note: Reporting device initally set to 0 [eth0] (merged)
Thursday 23 July 2009 01:32:01 PM IST  THREADMGMT[t3067745968]: ntop RUNSTATE: RUN(4)
Thursday 23 July 2009 01:32:01 PM IST  THREADMGMT[t2979797904]: NPS(1): Started thread for network packet sniffing [eth0]
Thursday 23 July 2009 01:32:01 PM IST  THREADMGMT[t3038710672]: SFP: Fingerprint scan thread running [p6744]
Thursday 23 July 2009 01:32:01 PM IST  THREADMGMT[t3030317968]: SIH: Idle host scan thread running [p6744]
Thursday 23 July 2009 01:32:01 PM IST  THREADMGMT[t2979797904]: NPS(eth0): pcapDispatch thread starting [p6744]
Thursday 23 July 2009 01:32:01 PM IST  THREADMGMT[t2979797904]: NPS(eth0): pcapDispatch thread running [p6744]
Thursday 23 July 2009 01:32:11 PM IST  **ERROR** RRD: Disabled - unable to create base directory (err 13, /var/lib/ntop/rrd)

---

### Post by bacil on 2009-07-23
first of all your ntop fails on creating directory /var/lib/ntop/rrd so check if directory exists and you have rights to it asuser nobody (thats user ntop is starting as)

---

### Post by bacil on 2009-07-23
OK,

JUST TESTED THIS.it appears that there is bug in install and /var/lib/ntop is installed with wrong rights there are two ways around it  

1. faster one
```
sudo chown -R nobody:nogroup /var/lib/ntop
```

2. slower but nicer
```
sudo chmod 755 /var/lib/ntop
```
```
sudo mkdir /var/lib/ntop/rrd
```
```
sudo chown -R nobody:nogroup /var/lib/ntop/rrd
```

and then you can run 

```
sudo ntop &
```

and connect to it on [http://localhost:3000](http://localhost:3000)

---

### Post by kpkeerthi on 2009-07-23
You could also try **vnstat**

---

