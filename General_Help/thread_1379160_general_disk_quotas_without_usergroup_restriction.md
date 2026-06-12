---
title: "general disk quotas without user/group restriction"
date: 2010-01-12
forum: General Help
---

### Post by rainerh on 2010-01-12
Hello everybody,

is it possible to limit the size of a specific folder independent of user or group? 
I want to restrict /var/log to a total size of 1GB. I don't think that the common approach to create a 1GB partition is the right way since it is possible that I want increase or decrease the limit in the near future.

Greetings,
Rainer

---

### Post by warfacegod on 2010-01-12
> **rainerh said:**
> Hello everybody,

is it possible to limit the size of a specific folder independent of user or group? 
I want to restrict /var/log to a total size of 1GB. I don't think that the common approach to create a 1GB partition is the right way since it is possible that I want increase or decrease the limit in the near future.

Greetings,
Rainer

Why would you want to do that? You would need 10s of thousands of files in there to even get to 1 GB. I just looked at mine, it's only 19 MB after 3 months.

---

### Post by rainerh on 2010-01-12
Hi there. 1GB was certainly just an example. I could also have written 100MB...

---

### Post by warfacegod on 2010-01-12
It should have something to do with allocating space for that folder. Search your help documentation. Although, I don't think limiting that particular folder would be a good idea, I've been wrong before.

---

