---
title: "problem creating a shared bashrc"
date: 2010-01-27
forum: General Help
---

### Post by tarekeldeeb on 2010-01-27
Hello all,

I administer a linux lab. A server experts /tools, all clients mount it.
On each client I add "/tools/otherbashrc" in /etc/bash.bashrc

In the otherbashrc file, commands like echo work on all client terminals, but exports do not!

please help

---

### Post by rnerwein on 2010-01-27
hi
i think you mean something like "export MYPATH".
then you have to sorce it in. that means a dot must be infront of /tools/... -->  . /tools/.....
ciao

---

### Post by tarekeldeeb on 2010-01-27
> **rnerwein said:**
> hi
i think you mean something like "export MYPATH".
then you have to sorce it in. that means a dot must be infront of /tools/... -->  . /tools/.....
ciao

source file
or . file

thanks .. this solved it =)

---

