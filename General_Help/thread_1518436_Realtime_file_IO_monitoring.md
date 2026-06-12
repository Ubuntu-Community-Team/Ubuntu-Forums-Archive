---
title: "Realtime file IO monitoring"
date: 2010-06-26
forum: General Help
---

### Post by vangop on 2010-06-26
Hi guys,
Can anybody suggest a tool similar to process monitor by sysinternals 
```
http://technet.microsoft.com/en-us/sysinternals/bb896645.aspx 
```
I need to have a full info on file IO a process does.
One of the applications I'm running doesn't see a file which is present. I want to capture its file IO activity to see what it checks, opens etc to find out what's wrong.

---

### Post by gmargo on 2010-06-26
See the **strace(1)** command.

---

### Post by vangop on 2010-06-27
Thanks, that's it!

---

