---
title: "Can't upgrade evince (wrong libc6 version)"
date: 2006-06-15
forum: General Help
---

### Post by jazzgossen on 2006-06-15
I have evince 0.5.2-0ubuntu3 and want to upgrade to version 0.5.3-0.1, which is in the repos. But when I try to (using synaptic), it complains that it has unresolvalbe dependencies. 

The first in the list of dependencies is libc6. Evince requires >= 2.3.6-6 but 2.3.6-0ubuntu20 is to be installed. libdbus and a bunch of other packages follow. 

What can I do?

---

### Post by magnusbb on 2006-06-15
You've got to have some unofficial repositories in your "sources.list". The latest version of Evince is still 0.5.2 in the official Dapper repositories.

---

