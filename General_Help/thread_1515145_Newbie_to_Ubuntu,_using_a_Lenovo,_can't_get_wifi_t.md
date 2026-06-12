---
title: "Newbie to Ubuntu, using a Lenovo, can't get wifi to turn on..."
date: 2010-06-21
forum: General Help
---

### Post by CarmillaMurray on 2010-06-21
I recently had a problem develop with my slightly more than a year old Lenovo S10 Idea book, that the only way to fix it was to do a hard drive wipe and install. Previously it was running windows, and before I decided to install ubuntu 9.10 from a cd, the wifi was working. 

Now I cannot get it to work, I've downloaded drivers from the disc. My means of connecting to the internet is with usually the wifi automatically detecting the signal source and then entering passwords as needed etc. 

How can I get it to do this again?

---

### Post by chizzledfrmstone on 2010-06-21
I'm having the same problem. Have you installed the Proprietary drivers?

[http://ubuntuforums.org/showthread.php?p=9493710&posted=1#post9493710](http://ubuntuforums.org/showthread.php?p=9493710&posted=1#post9493710)

---

### Post by Serpher on 2010-06-22
Post the output of:

```
lspci|grep Network
```

---

