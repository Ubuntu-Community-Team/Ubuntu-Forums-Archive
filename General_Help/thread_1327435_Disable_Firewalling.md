---
title: "Disable Firewalling"
date: 2009-11-15
forum: General Help
---

### Post by DavidCDean on 2009-11-15
I have an internal machine here I need to disable firewalling for.  My understanding is that I need to do this by modifying chains for iptables.

I've installed Firestarter but it has never worked in previous Ubuntu releases insofar as I've never gotten changes made with it to persist. 

So my guess is that I need to edit the chains manually to open everything up.  How do I flush all the default rules and set it to ALLOW everything, from everywhere, to everywhere?

---

### Post by pootan on 2009-11-15
```
sudo ufw default allow
```

Type that in the terminal.

---

### Post by DavidCDean on 2009-11-15
Excellent, thanks!

---

