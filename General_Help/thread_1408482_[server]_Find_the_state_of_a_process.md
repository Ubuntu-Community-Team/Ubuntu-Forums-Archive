---
title: "[server] Find the state of a process"
date: 2010-02-16
forum: General Help
---

### Post by blazemore on 2010-02-16
On server (no GUI) how can I find the state (running, sleeping, zombie) of a given process, by giving a process name or PID?

---

### Post by rnerwein on 2010-02-16
hi
i think: ps -elf | grep what you want  then you will see the  WCHAN
ciao

---

### Post by blazemore on 2010-02-16
NVM I worked it out,
```
ps -C foo -o stat=
```

does the trick. What do the different process codes mean?

---

### Post by rnerwein on 2010-02-16
hi
a exlanitio of the process codes you will find by using --> man ps
the description will be found at: PROCESS STATE CODES 
e.g. in the first row: Ss+ means "S=Sleeping, s=session leader, += foreground process group leader

have fun
ciao

---

