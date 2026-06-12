---
title: "list master process"
date: 2009-12-29
forum: General Help
---

### Post by razzer on 2009-12-29
Hello. How could i List all the "physical" files that the master process for Postfix currently has open on my ubuntu server ?

---

### Post by iponeverything on 2009-12-29
lsof -p <pid of postfix process>

---

