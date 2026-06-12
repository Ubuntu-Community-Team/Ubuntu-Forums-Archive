---
title: "Set Firefox cache to Ramdisk in Ub. 10.4"
date: 2010-04-19
forum: General Help
---

### Post by ProDigit on 2010-04-19
I know the topic is old, but has anything changed in 10.4 to set firefox cache to a ram disk?

As I understand /dev/shm is a ramdisk allocated by Ubuntu Kernel.

But how can we set Firefoxe's cache directory to this one?
I couldn't find any setting in about:config in FireFox.

Thanks!

---

### Post by linden940 on 2010-04-19
try this

[http://www.ghacks.net/2007/12/14/use-a-ramdisk-to-increase-firefox-security/](http://www.ghacks.net/2007/12/14/use-a-ramdisk-to-increase-firefox-security/)

---

### Post by ProDigit on 2010-04-19
> **linden940 said:**
> try this

[http://www.ghacks.net/2007/12/14/use-a-ramdisk-to-increase-firefox-security/](http://www.ghacks.net/2007/12/14/use-a-ramdisk-to-increase-firefox-security/)

Thank you, but that is a Windows solution.
I'm running Ubuntu 10.4.

---

### Post by dcstar on 2010-04-20
> **ProDigit said:**
> I know the topic is old, but has anything changed in 10.4 to set firefox cache to a ram disk?

As I understand /dev/shm is a ramdisk allocated by Ubuntu Kernel.

But how can we set Firefoxe's cache directory to this one?
I couldn't find any setting in about:config in FireFox.


Look harder: 

```
browser.cache.memory.capacity
browser.cache.memory.enable
```

---

### Post by ProDigit on 2010-04-21
> **dcstar said:**
> Look harder: 

```
browser.cache.memory.capacity
browser.cache.memory.enable
```

That does not tell me where the cache is used.
I would love to open files from cache or be able to view it.

---

### Post by ario on 2011-02-04
I found that!
It is like this:
type about:config in address bar of firefox. promise it you will never ruin your firefox!
Right click on the table grid. 
Select New.
Enter **browser.cache.disk.parent_directory** as name. Make sure you enter the name correctly or else, it will not work!
Enter address of your mounted ram drive as value. To find out how to create and mount a ram drive using tmpfs you can search more):P

---

