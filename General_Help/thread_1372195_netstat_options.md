---
title: "netstat options"
date: 2010-01-04
forum: General Help
---

### Post by cucuru on 2010-01-04
hello, I want to see all the connections between my computer and other, Does it exist any option with netstat (or other) to see just this IP?

It is very difficult look for this address any time, I have a lot!

Thank you. Regards

---

### Post by rnerwein on 2010-01-04
hi
there is a nice tool (apt-get install iftop)
i think it belongs to your behaivor
ciao

---

### Post by cucuru on 2010-01-05
Thank you, I tried use together netstat and grep and it worked perfect, if somebody needs it:

sudo netstat -n | grep 'xx.xx.xx.xx'

-n is for numerical IP.

Regards

---

