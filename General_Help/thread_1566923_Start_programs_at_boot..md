---
title: "Start programs at boot."
date: 2010-09-03
forum: General Help
---

### Post by konstg on 2010-09-03
Hello guys! 
 
Got a problem :confused:. I have a VPS with Ubuntu 10.04 and acces to it via putty. Besides postgres database there should be running two java program which I wrote. It works fine from command line. But I need them to start automatically at boot time. Can anybody help me?
 
Thanks in advance,
Konstantin.

---

### Post by Elfy on 2010-09-03
Add them both to startup apps 

System - Preference - Startup Applications

---

### Post by konstg on 2010-09-03
> **forestpiskie said:**
> Add them both to startup apps 
 
System - Preference - Startup Applications
 
 
Yes, but I have only command line via putty, no desktop.

---

### Post by Elfy on 2010-09-03
Sorry - not awake yet.

Try adding it to /etc/rc.local

---

### Post by konstg on 2010-09-03
> **forestpiskie said:**
> Sorry - not awake yet.
 
Try adding it to /etc/rc.local
 
Done! And added '&' after the end of every invoke.
Thanks a lot, man! ;)

---

### Post by Elfy on 2010-09-03
welcome - I am at least awake now ...

---

