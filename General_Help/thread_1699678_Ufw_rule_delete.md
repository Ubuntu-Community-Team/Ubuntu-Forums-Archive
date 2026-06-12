---
title: "Ufw rule delete"
date: 2011-03-04
forum: General Help
---

### Post by dragos2 on 2011-03-04
How to delete this ufw rule in Ubuntu 8.04 :
```

To                         Action  From
--                         ------  ----
1521:tcp                   ALLOW   x.y.z.w

```

I tried this:
```

ufw delete allow proto tcp from x.y.z.w port 1521

```

---

### Post by prshah on 2011-03-04
> **dragos2 said:**
> How to delete this ufw rule in Ubuntu 8.04 :

```
sudo ufw status numbered
sudo ufw delete <number>
```

The first command will list the ufw rules with numbers; the second command (with the corresponding number) will delete the relevant rule.

---

### Post by dragos2 on 2011-03-04
> **prshah said:**
> ```
sudo ufw status numbered
sudo ufw delete <number>
```The first command will list the ufw rules with numbers; the second command (with the corresponding number) will delete the relevant rule.

Solved:
```

ufw delete allow from x.y.z.q to any port 1521

```

status numbered is not implemented in ufw for 8.04.

---

