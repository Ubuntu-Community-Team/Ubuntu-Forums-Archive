---
title: "EASYNOTE TS: ubuntu 11.04 Ram problem..."
date: 2011-07-05
forum: General Help
---

### Post by omeraygor on 2011-07-05
i have packardbell EASYNOTE TS.i am using ubuntu 11.04.
it has 8 gb ram. But i can see only 2.3 gb useable. 
What can be prblem?

[http://www.flickr.com/photos/23404611@N08/5905295056/](http://www.flickr.com/photos/23404611@N08/5905295056/)

---

### Post by mörgæs on 2011-07-06
Please post the output from **free -m**.

---

### Post by omeraygor on 2011-07-07
omeraygor@blackperl:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2373       1677        696          0        121        903
-/+ buffers/cache:        652       1721
Swap:         8042          0       8042

---

### Post by plucky on 2011-07-07
> **omeraygor said:**
> i have packardbell EASYNOTE TS.i am using ubuntu 11.04.
it has 8 gb ram. But i can see only 2.3 gb useable. 
What can be prblem?

[http://www.flickr.com/photos/23404611@N08/5905295056/](http://www.flickr.com/photos/23404611@N08/5905295056/)

Did you install the 32-bit version?


Post output of ```
uname -a
```

Either use the PAE kernel or upgrade to the 64-bit version of Natty.

Good Luck

---

### Post by omeraygor on 2011-07-08
omeraygor@blackperl:~$ uname -a
Linux blackperl 2.6.38-8-generic #42-Ubuntu SMP Mon Apr 11 03:31:50 UTC 2011 i686 i686 i386 GNU/Linux

yes i am using 32 bit ubuntu.

---

### Post by mörgæs on 2011-07-08
Then try a live boot of the 64 bit version.

---

### Post by omeraygor on 2011-07-26
i setup 64 bit ubuntu. and solved my problem... THANKS...

---

