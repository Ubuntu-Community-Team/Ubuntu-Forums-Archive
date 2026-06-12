---
title: "SHUT DOWN problems..!"
date: 2009-09-05
forum: General Help
---

### Post by arunprasad13 on 2009-09-05
i recently installed ubuntu 8.04...eversince i installed it i have a problem with the SHUT DOWN option, it restarts the computer.

i tried, 

1.init 0
2.poweroff  on the CLI but all of them would only restart the computer none of them shuts it down.

---

### Post by DFlame on 2009-09-05
I assume you get the same result from:

```
sudo shutdown -h now
```

?

---

### Post by arunprasad13 on 2009-09-06
ya...cant fix it

i tried all these methods also

The first one (stopping networking)
The second (acpi=force) 
The third (apm power_off=1)

---

