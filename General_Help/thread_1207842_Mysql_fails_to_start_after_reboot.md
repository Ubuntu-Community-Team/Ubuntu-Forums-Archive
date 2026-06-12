---
title: "Mysql fails to start after reboot"
date: 2009-07-08
forum: General Help
---

### Post by pfunkman on 2009-07-08
I have run into an issue where mysql will not start after rebooting the machine unless i completely reinstall all the mysql packages.

The log at /var/logs/mysql.log is completely empty.

Im a bit lost here, what could be the issue?

---

### Post by vikkikanhaua on 2009-07-08
might be u can install bum{boot up manager} to check ur all processes which are started when the system boots

---

### Post by pfunkman on 2009-07-08
> **vikkikanhaua said:**
> might be u can install bum{boot up manager} to check ur all processes which are started when the system boots

My issue is not that it dont start with the computer. My issue is once i restart it wont start at all until i completely reinstall it.

---

### Post by pfunkman on 2009-07-08
Well i just reformatted and reinstalled ubuntu and its doing it still.

Not sure what to think at this point, works when its installed just fine as soon as i restart poof:

```
* Starting MySQL database server mysqld                                 [fail] 
```

---

### Post by pfunkman on 2009-07-08
Just did a fresh install and instead of installing each component through synaptic i used sudo tasksel install lamp-server and all is well.

---

