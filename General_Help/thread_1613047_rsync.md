---
title: "rsync"
date: 2010-11-04
forum: General Help
---

### Post by th1bill on 2010-11-04
I give up!  My main computer is home and my back-up is my old unit named mepis.  After a week and a half of trying I yield to the Superior Minds.  Below is my last attempt to back-up my Documents folder of the Ubuntu unit to the older Mepis for insurance. 


> th1bill@home:~$ rsync -avP /Documents/* th1bill@mepis:home/th1bill/Backups
ssh: connect to host mepis port 22: Connection timed out
rsync: connection unexpectedly closed (0 bytes received so far) [sender]
rsync error: unexplained error (code 255) at io.c(601) [sender=3.0.7]
th1bill@home:~$ 


I am one lost puppy and will appreciate any help.

---

### Post by TiBaal89 on 2010-11-04
Perhaps a silly question... but are you able to reach the other machine via ssh? i.e.

```
ssh th1bill@mepis
```

---

### Post by th1bill on 2010-11-04
I didn't find a probing question silly and the answer is no.  I can't ping it either and when I use the address 192,168.1.66 I still get no results.  If I ping th1bill@home or at 192.168.1.67 from the mepis unit it pings just fine.

---

