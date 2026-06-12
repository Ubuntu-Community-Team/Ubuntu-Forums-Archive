---
title: "Run command during user activity/idle (to suspend f@h)"
date: 2010-04-20
forum: General Help
---

### Post by undecim on 2010-04-20
folding@home has been slowing down my quad core Kubuntu system. I can start/stop it with origami, but I need to know how to run the start/stop commands when the user becomes idle or active.

Or, if I can tell if any user logged in with KDM (since I don't want ssh to stop f@h) is active from a script, I can write one that will do all I need.

I can edit sudoers if the commands have to be run as the user. There's only one user I'm worried about making happy (it's the one everyone in the family shares)

Thanks in advance.

---

### Post by dcstar on 2010-04-21
> **undecim said:**
> folding@home has been slowing down my quad core Kubuntu system. I can start/stop it with origami, but I need to know how to run the start/stop commands when the user becomes idle or active.

Or, if I can tell if any user logged in with KDM (since I don't want ssh to stop f@h) is active from a script, I can write one that will do all I need.

I can edit sudoers if the commands have to be run as the user. There's only one user I'm worried about making happy (it's the one everyone in the family shares)

Thanks in advance.

```
man w
```

---

### Post by undecim on 2010-04-21
> **dcstar said:**
> ```
man w
```

w just gives me "?xdm?" as the idle time for the user.

---

### Post by patchwork on 2010-04-21
It might be overkill, but you can use monit to monitor the folding@home process, and based on load level or other factors, start or stop the process.

---

