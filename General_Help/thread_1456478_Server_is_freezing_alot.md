---
title: "Server is freezing alot"
date: 2010-04-17
forum: General Help
---

### Post by Speedvrod on 2010-04-17
Hi all.

I hve a server co-located in a datacenter, which are freezing very often. First, it had kernel panics about some Aiee not syncing - killing interrupt handler. Now, its freezing and i have no idea why. I have another server in same center aswell which is running fine without any problems. The server that has problems is a AMD Phenom II 965 machine, the other server is a Dell R210. A guy that Works in the datacenter has told me that it could be a memory leak.. If you need any other Info, please ask!

Thanks

Chris

---

### Post by gmargo on 2010-04-17
A memory leak?  Nonsense.  You have bad hardware, probably bad RAM.  Or bad RAM or CPU voltages.

---

### Post by Speedvrod on 2010-04-17
Okay, is there any ways to debug the hardware through console?

---

### Post by Speedvrod on 2010-04-25
No one is able to help me with this? :confused:

---

### Post by P4man on 2010-04-25
Start by checking your log files in /var/log and see if they provide a pointer to what is causing the freezes. Frankly, it could be anything, from bad ram to a bad harddisk to overheating to a bug. Check your log files so we have a starting point at least.

---

