---
title: "Network Driver?"
date: 2011-08-18
forum: General Help
---

### Post by galacticaboy on 2011-08-18
How do I figure out what network driver I have? Is there a terminal command that will tell me what driver it is called?

---

### Post by grahammechanical on 2011-08-18
```
lshw -C network
```

It will take a few seconds to produce results and warn you that you should be issuing the command as superuser

Regards

---

### Post by galacticaboy on 2011-08-18
> **grahammechanical said:**
> ```
lshw -C network
```

It will take a few seconds to produce results and warn you that you should be issuing the command as superuser

Regards

I did that command and I get this:

```
bash: lshw: command not found

```

---

### Post by Haneef Mubarak on 2011-08-18
Odd. Try
```
sudo lshw -C network
```
and if that doesn't work, post the result, try
```
sudo apt-get install lshw
```
post the code you get from that and then repeat
```
sudo lshw -C network
```

---

