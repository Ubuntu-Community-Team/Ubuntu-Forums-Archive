---
title: "PHP import script speed"
date: 2011-11-02
forum: General Help
---

### Post by jon23d on 2011-11-02
I am running a script that imports a bunch of fixtures into a database. When I run it on the server, it takes about 2 minutes, but when I run it locally, it easily takes 15-20 minutes.

I have allocated more memory in php.ini locally, and I have about 6gigs more memory locally anyway.  CPU and memory utilization are low, and the amount of data being committed to disk is actually pretty low, so I suspect write speed isn't an issue.  CPU utilization is sitting around 5% for each of the four, and memory utilization is less than 50% total, including gnome, dev tools, running scripts, etc.

Is there something that I am missing?  My my.cnf seems to be about the same locally as remotely too.

Thanks

---

