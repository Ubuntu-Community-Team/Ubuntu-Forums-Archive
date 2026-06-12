---
title: "how to change the order of startup programs"
date: 2010-04-12
forum: General Help
---

### Post by eg0n on 2010-04-12
I have noticed a few problems when some screenlets are loaded before some others. I think that "Startup Applications Preferences" should have an option to arrange the order of their execution. If you have any ideas of how I could do that thing manually, it would be really helpful.

---

### Post by change_mode on 2010-04-12
You can easily do this by writing a script that loads the programs in whatever order you want.

```
#!/bin/bash
program1
sleep 2
program2
sleep 2
program3
[...]
```

Save as startup.sh, make it executable, then put that script in startup applications.

---

### Post by Helkaluin on 2010-04-12
Or delay specific items with ```
sh -c "sleep *seconds*; exec *command*"
```

The above is also useful for whatever apps that you don't need immediately when you log in.

---

### Post by eg0n on 2010-04-14
thanx!!

---

### Post by hariks0 on 2010-07-17
> **Helkaluin said:**
> Or delay specific items with ```
sh -c "sleep *seconds*; exec *command*"
```

The above is also useful for whatever apps that you don't need immediately when you log in.

Editing the command in the Properties of the item in Desktop Sessions to incorporate the above will just work. No need for a script if you need only a single program to start up later.
;)

---

