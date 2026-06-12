---
title: "Why is more RAM used without database server running?"
date: 2011-10-26
forum: General Help
---

### Post by ratcheer on 2011-10-26
I think this is weird. After the PostgreSQL database server is shut down, my system uses more RAM than when it was running. Here are the figures from a freshly booted system:

```
tim@tim-oneiric:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7984        903       7081          0        116        227
-/+ buffers/cache:        559       7425
Swap:         8191          0       8191
tim@tim-oneiric:~$ sudo service postgresql stop
[sudo] password for tim: 
 * Stopping PostgreSQL 9.1 database server                                                                           [ OK ] 
tim@tim-oneiric:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7984        946       7038          0        116        222
-/+ buffers/cache:        607       7377
Swap:         8191          0       8191
```

With the database server running, it had 559 MB used memory, but after shutting it down, 607 MB was used. I just wonder why?

Tim

---

### Post by jnorthr on 2011-10-26
Like all modern operating systems, linux tends to keep as many pieces of code and data in physical ram as possible. This is governed by a setting known as swappiness. It is a value that can be set either for just the current bootup or can be made permanent. you can google ubuntu swappiness to read more. In your particular case, not using a database server leaves more room for more big pieces that can fit comfortably into ram. With d/b running fewer big pieces will fit and the o/s spends more time (and runs more slowly) by swapping bits in around the d/b server.

---

### Post by Slim Odds on 2011-10-26
It's really too bad this has to be re-explained each and every day.

[http://www.linuxatemyram.com/](http://www.linuxatemyram.com/)

---

### Post by ratcheer on 2011-10-26
Ok, thanks guys.

Tim

---

