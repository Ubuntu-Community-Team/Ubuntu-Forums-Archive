---
title: "mysql cluster load sharing"
date: 2009-08-10
forum: General Help
---

### Post by kiminaiseah on 2009-08-10
hi, i am looking for an solutions that can distribute the mysql load into other mysql server with in the network without touching the kernel, the problem is, we have a millions and thousand of records keeping in mysql db, and we hired some programmers that can manipulate that record into billing/ history per transaction/ etc. etc.., the problem encounter here when simple query runs, the machine we had (2x xeon 3100 | 12GB RAM) and its turn into misery it having cpu load 80, cpu usage 100%, and the query takes 5-10 minutes before you see something readable.. 

TIA.

---

### Post by P4man on 2009-08-10
Hire better programers or db admin :)

Im only half kidding;  if you really need (and your app can use) clustering and/or load balancing, I would ask help in a MySQL forum. I don't know much about it, but I do know there is no easy way to make several machines run a single query. I also suspect you don't need to if there is only 1 or a few clients connected to it, but that your db needs some work.

---

