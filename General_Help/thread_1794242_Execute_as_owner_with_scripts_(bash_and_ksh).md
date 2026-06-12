---
title: "Execute as owner with scripts (bash and ksh)"
date: 2011-06-30
forum: General Help
---

### Post by couling on 2011-06-30
Hi All

I've read a number of times about the security hole that makes setting a script to execute as owner dangerous.

The problem used to be that if someone made a symlink to your script, called it but changed the symlink to point to something else, the kernel might execute ksh or bash as the owner of your script, but ksh or bash would follow the symlink to whatever they changed the link to and run that instead.

Does anyone know if anything has been done to fix this, or is it still a problem?

Regards

---

