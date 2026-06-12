---
title: "Broken Package - Help Please"
date: 2009-09-23
forum: General Help
---

### Post by mikeody on 2009-09-23
Hello All,
Am relatively new to Ubuntu [Jaunty].
I downloaded and tried to install a .deb application. Halfway through it stopped and now when I go into Synaptic Package Manager I always get a message that says "1 Broken Package - Use 'Broken' Filter to locate it".
When I go to Settings/Filters and select 'Broken' and then 'OK' I get a huge list of applications - some installed some not.
How do I find the "Broken Package" please ? And what should I do then ?
Thanks.

---

### Post by MelDJ on 2009-09-23
did you go to custom filters?

---

### Post by wojox on 2009-09-23
Open a terminal:

```
sudo dpkg --configure -a
```

---

