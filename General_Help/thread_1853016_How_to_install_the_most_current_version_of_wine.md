---
title: "How to install the most current version of wine?"
date: 2011-10-01
forum: General Help
---

### Post by beanman25 on 2011-10-01
First off, I haven't posted here in ages. I just installed Ubuntu on my laptop. I can't get to comfortable as I'm getting a new HDD for my laptop, so I'm mainly just trying to figure out how to get everything installed so it's easier with the new HDD. 

I followed the steps from Wine HQ to add the PPA Repository but whenever I try to install Wine 1.3/1.2, nothing happens. The Software Center icon shakes but nothing pops up.

If anyone could assist me, that would be fantastic.

Thanks!

---

### Post by jon zendatta on 2011-10-01
```
sudo apt-get install wine
```

---

### Post by prodigy_ on 2011-10-01
> **jon zendatta said:**
> sudo apt-get install wine
This will install 1.2. If you want 1.3 (which is probably preferable considering rapid development and long release cycle), it's:
```
sudo apt-get install wine1.3
```
In any case don't forget to run ```
sudo apt-get update
``` first.

---

