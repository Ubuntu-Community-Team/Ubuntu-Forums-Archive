---
title: "How much memory do your ubuntu use"
date: 2010-09-14
forum: General Help
---

### Post by permant on 2010-09-14
Hi everyone:
    a problem puzzle me for a long time, how much memory a ubuntu machine use? I use the 'top' to query,about 1.5G was used, 500M free. surprise!
System monitor show that only 400M memory are used, which one was right??

---

### Post by borth92 on 2010-09-14
if i was you i would dearly hope that the one that says 99% of cpu is going to nautilis. I use about 633 MBs of memory, but thats using firefox/compiz/thunderbird/banshee. I would do you have compiz enabled?

---

### Post by permant on 2010-09-14
> **borth92 said:**
> if i was you i would dearly hope that the one that says 99% of cpu is going to nautilis. I use about 633 MBs of memory, but thats using firefox/compiz/thunderbird/banshee. I would do you have compiz enabled?
compiz is not enabled. only firefox is open to browser this web page. By the way, would you mind telling me how you examine your memory usage?

---

### Post by asmoore82 on 2010-09-14
`top` memory usage includes the filesystem cache, which is not really used RAM
as it can be dumped at a moment's notice if needed for software usage.

You have to take the usage from `top` and subtract the "cached" to get the same result as "System Monitor"

You can also use the command `free` to get the same RAM data as `top`

I just found out that now `free` will do the math for you! -
on the "-/+ buffers/cache:" line.

---

