---
title: "lsof, report only PIDs?"
date: 2009-12-27
forum: General Help
---

### Post by abeisgreat on 2009-12-27
Hello, right now, when running
```

lsof /dev/video

```
I get an output like 
```

COMMAND   PID USER   FD   TYPE DEVICE SIZE/OFF NODE NAME
cat     30117  abe    3r   CHR   81,0      0t0 5657 /dev/video0

```
What I would like is it to return something like
```

COMMAND   PID
cat     30117

```
or even just
```

30117

```
Is this possible, or will I need to parse the output of the command?

---

### Post by falconindy on 2009-12-27
Sure sure, easily done.
```
lsof <args> | awk '{printf "%20s\t%s\n",$1, $2}'
```

---

### Post by abeisgreat on 2009-12-27
> **falconindy said:**
> Sure sure, easily done.
```
lsof <args> | awk '{printf "%8s\t%s\n",$1, $2}'
```

Thanks matey

---

### Post by dcstar on 2009-12-28
> **falconindy said:**
> Sure sure, easily done.
```
lsof <args> | awk '{printf "%20s\t%s\n",$1, $2}'
```
or:
```
lsof <args> | cut -d" " -f 1,2
```

---

### Post by falconindy on 2009-12-28
> **dcstar said:**
> or:
```
lsof <args> | cut -d" " -f 1,2
```

This'll fail because fields are separated by more than 1 space.

---

### Post by dcstar on 2009-12-28
> **falconindy said:**
> This'll fail because fields are separated by more than 1 space.

Quite right:

```
lsof <params> | cut -b 1-10,11-16
```

---

