---
title: "ScanMem error"
date: 2011-04-25
forum: General Help
---

### Post by MrMicrowave on 2011-04-25
Hello , was wondering if anyone could help me with a program called Scanmem, it keeps giving me an error when searching something.

here is an example:

0> pid 2746
info: maps file located at /proc/2746/maps opened.
info: 82 suitable regions found.
0> 10
error: failed to attach to 2746, Operation not permitted
error: failed to search target address space.

thanks for any support :)

---

### Post by withjigs on 2011-04-25
Just a guess,
Is the process you are trying to scan running as root?
If so you could trying using scanmem as root.

However, I am not very sure about this. Let me know if get it working!

regards,
jigs

---

### Post by MrMicrowave on 2011-04-25
> **withjigs said:**
> Just a guess,
Is the process you are trying to scan running as root?
If so you could trying using scanmem as root.

However, I am not very sure about this. Let me know if get it working!

regards,
jigs

thanks! ran sudo and it worked :)

---

### Post by erikthedrink on 2011-08-31
Worked for me, too.  Thanks, Withjigs!:popcorn:

---

