---
title: "Software source issues"
date: 2010-05-26
forum: General Help
---

### Post by wesleybishop on 2010-05-26
Okay I am having conflicts in my software sources some maybe out of date but I am not sure how to tell which ones are. Is there a program that solves these problems. I have Ubuntu 10.4

---

### Post by drs305 on 2010-05-26
If you just want a generic sources.list for your release of Ubuntu, you can visit this site which can generate one for you.

[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

Or if you give us your version and post your current /etc/apt/sources.list we can look at it. 

Note: You may also have sources in your /etc/apt/sources.list.d folder.

---

### Post by wesleybishop on 2010-05-28
How do I find the list so I can copy it here?

---

### Post by plucky on 2010-05-29
> **wesleybishop said:**
> How do I find the list so I can copy it here?

From a terminal ```
cat /etc/apt/sources.list
cat /etc/apt/sources.list.d/*.list
```


Good Luck

---

### Post by wesleybishop on 2010-06-28
Thanks for everyones help :)

---

