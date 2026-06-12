---
title: "Can't Update"
date: 2010-01-07
forum: General Help
---

### Post by ripper9100 on 2010-01-07
Hi,

I'm using Ubuntu 9.04 and I'm having a few problems. Update Manager, Synaptic Package Manager, and Add/Remove start but immediately grey out and 10 seconds later close automatically. I'm only having issues with these applications. 

From a suggestion I read in this forum I tried this command on the terminal
*sudo aptitude update && sudo aptitude full-upgrade* and got a Bus Error.

Anybody know what's wrong.

---

### Post by jmszr on 2010-01-07
ripper9100,

I had a similar problem and this was the fix for me:

```
sudo rm /var/cache/apt/*.bin  
```

Hope that helps.

---

### Post by ripper9100 on 2010-01-07
Fixed it thank you.

---

