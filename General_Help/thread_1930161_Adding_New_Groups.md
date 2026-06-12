---
title: "Adding New Groups"
date: 2012-02-23
forum: General Help
---

### Post by AndrewMayes on 2012-02-23
Hi Guys

I'm having issues creating a new user on one of my ubuntu servers. for some reason when he logs in he is not able to run any bash commands. However if I change his default user group to a previously created group, then his login works. does anybody perhaps have any idea why this would be?

---

### Post by dcstar on 2012-02-25
> **AndrewMayes said:**
> Hi Guys

I'm having issues creating a new user on one of my ubuntu servers. for some reason when he logs in he is not able to run any bash commands. However if I change his default user group to a previously created group, then his login works. does anybody perhaps have any idea why this would be?
This will show you the differences between a correctly working user and your new user:
```
groups <user>
```

---

