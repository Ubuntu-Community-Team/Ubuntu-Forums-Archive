---
title: "ls -ldR"
date: 2011-08-04
forum: General Help
---

### Post by satish_j on 2011-08-04
Can i use 
```

ls -ldR /

```
to list all directories(recursively)under root?

---

### Post by hakermania on 2011-08-04
Hmmm, wihtout the -d it lists all the files [tested], with the -d it lists nothing (only / )  :P

---

### Post by satish_j on 2011-08-04
> **hakermania said:**
> Hmmm, wihtout the -d it lists all the files [tested], with the -d it lists nothing (only / )  :P

Can you post output file of foll command from your system
```

ls -Rl / | egrep '^d' > /home/dflt_perm.txt

```

---

