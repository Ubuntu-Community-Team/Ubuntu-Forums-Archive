---
title: "openssh"
date: 2010-02-22
forum: General Help
---

### Post by prabhanjan2906 on 2010-02-22
open ssh is not working properly even though it exists. the manual page for ssh is displaying. ssh master is not working. should i download the package? if so what is the command for downloading.

---

### Post by nixclusive on 2010-02-22
A few questions,
1. What are the steps you are executing to use openssh?
2. Are you getting any error messages? If so, can you paste them here?
3. Are you trying to setup an openssh server? or are you trying to connect to some other openssh server?

Regards.

---

### Post by prabhanjan2906 on 2010-02-23
we are setting up a cloud. we have a master computer that is named as master. from the master computer we have to ssh into the master itself. it is showing port 22 connection refused.
thanks in advance

---

### Post by nixclusive on 2010-02-23
> port 22 connection refused
That means there's no program listening on that port. You need to make sure that an ssh **server** is up and running on the target machine.

---

### Post by tubasoldier on 2010-02-23
The SSH server is not installed by default on Ubuntu. It may be on ubuntu-server edition but definitely not on the desktop.

---

### Post by nixclusive on 2010-02-23
Yes. The ssh server is not installed by default on the desktop edition although the client is present. You can install "openssh-server" from the package management system for an ssh server. :)

---

