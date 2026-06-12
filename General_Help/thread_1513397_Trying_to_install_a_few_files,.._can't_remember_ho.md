---
title: "Trying to install a few files,.. can't remember how to do it.."
date: 2010-06-19
forum: General Help
---

### Post by Zerocool Djx on 2010-06-19
libssh-2
libssh-2-dev

Anyone done this before? They are in the repositories but saying:

$ sudo aptitude install libssh-2
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
$ sudo aptitude install libssh-2
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

---

### Post by oldos2er on 2010-06-19
Only one package management program can be open at one time; this includes Synaptic, Ubuntu Software Center, Update manager, etc.

---

### Post by tekkidd on 2010-06-19
that means another package manager is working.

---

### Post by Zerocool Djx on 2010-06-19
gotcha,.. hmm,.. no it says it isn't in the repos... anyone know where to get it?

---

### Post by Zerocool Djx on 2010-06-19
ok so apparently I already have these files but they might not be enabled? hows this work?

---

### Post by oldos2er on 2010-06-19
What exactly are you trying to do?

---

