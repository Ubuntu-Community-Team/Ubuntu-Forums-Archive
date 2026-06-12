---
title: "string manipulation"
date: 2009-11-12
forum: General Help
---

### Post by thestig_992 on 2009-11-12
I have a string that a get from ifconfig that i want to cut up and paste in a file, then add up. An example of the string would be:

```
          RX bytes:122448301 (122.4 MB)  TX bytes:8376569 (8.3 MB)
```

this comes from the command:
```
(computername):~$ ifconfig eth0|grep "RX bytes"

```

Is it possible to cut out only the numbers (the number of bytes, not mb, as in 122448301 and 8376569), and then store them as separate variables?

---

### Post by mobilediesel on 2009-11-12
> **thestig_992 said:**
> I have a string that a get from ifconfig that i want to cut up and paste in a file, then add up. An example of the string would be:

```
          RX bytes:122448301 (122.4 MB)  TX bytes:8376569 (8.3 MB)
```

this comes from the command:
```
(computername):~$ ifconfig eth0|grep "RX bytes"

```

Is it possible to cut out only the numbers (the number of bytes, not mb, as in 122448301 and 8376569), and then store them as separate variables?

This should do it:
```
xt=$(ifconfig eth0|grep "RX bytes")
rx=$(echo $xt|sed 's/\([^:]*:\)\([^ ]*\).*/\2/')
tx=$(echo $xt|sed 's/\([^:]*:[^:]*:\)\([^ ]*\).*/\2/')

```

---

### Post by thestig_992 on 2009-11-12
thanks, works perfectly.

I have 2 more questions:

1. Is it possible to run a specific shell script when i shutdown? It has to be the first thing that happens at shutdown, before any other apps are closed.

2. How do I output a message through the new notification system? Is it a zenity command, or something else?

---

