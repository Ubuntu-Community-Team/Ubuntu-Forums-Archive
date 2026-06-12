---
title: "Listing Background jobs from all terminals ."
date: 2010-04-19
forum: General Help
---

### Post by rainbow99984 on 2010-04-19
Hi, I'm running Ubuntu 9.10. I have 3-4 gnome-terminal running depending on task,
 I run few commands as background on all of the terminals. 
for some reason I need to close it or use other Terminals but when using "jobs" it shows jobs under current terminals only. 
Is there any way to see jobs list running over all the terminals which are either "running or closed". 
Thanks.
Rahul

---

### Post by dcstar on 2010-04-19
> **rainbow99984 said:**
> Hi, I'm running Ubuntu 9.10. I have 3-4 gnome-terminal running depending on task,
 I run few commands as background on all of the terminals. 
for some reason I need to close it or use other Terminals but when using "jobs" it shows jobs under current terminals only. 
Is there any way to see jobs list running over all the terminals which are either "running or closed". 
Thanks.
Rahul

```
ps -ef | grep pts
```

---

### Post by rainbow99984 on 2010-04-19
This works, Thanks.:)

---

