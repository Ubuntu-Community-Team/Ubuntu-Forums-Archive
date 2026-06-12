---
title: "accedental wrong modprobe"
date: 2006-06-07
forum: General Help
---

### Post by mrweirdo on 2006-06-07
I just installed lm-sensors from reading a guide on this forum however I wasnt thinking and typed in the wrong modprobe modules before inserting the corect ones. Does anyone know how I can remove those? or is even something to worry about?

---

### Post by christhemonkey on 2006-06-07
To remove modules:

```
sudo rmmod modules_you_modprobed 
```


You may want to see a list of modules you have loaded, (in case you forgot what it was called!);

```
lsmod 
```

---

### Post by thasheep on 2006-06-07
Loading unneeded modules is a waste but does no damage. As christthemonkey said, rmmod can remove them.

---

### Post by mrweirdo on 2006-06-07
thnx for the help :)

---

### Post by christhemonkey on 2006-06-07
No problem.

---

