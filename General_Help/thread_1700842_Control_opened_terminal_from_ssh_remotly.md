---
title: "Control opened terminal from ssh remotly"
date: 2011-03-05
forum: General Help
---

### Post by wbuntu on 2011-03-05
Lets say I have SCP open on transfer..
I'm logging in from remote computer thru ssh..
Is it possible that I can see the progress of the transfer?
Is it possible to take over that terminal and make it available to me remotely using ssh?
Thanks.

---

### Post by Habitual on 2011-03-05
scp -p will show progress

---

### Post by seawolf167 on 2011-03-05
> **wbuntu said:**
> Is it possible to take over that terminal and make it available to me remotely using ssh?

I'm not exactly sure what you're aiming for - but if you start a process with 

```
screen
```

then detach it you can reattach to that terminal (and it's running processes) whenever/wherever you want (i.e. through any ssh session)

---

