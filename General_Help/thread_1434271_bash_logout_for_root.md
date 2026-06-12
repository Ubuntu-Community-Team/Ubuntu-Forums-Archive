---
title: "bash_logout for root"
date: 2010-03-20
forum: General Help
---

### Post by Vishal Agarwal on 2010-03-20
Hi ,

While I check the root folder, I did not see the .bash_logout file. the same is present in other users folders.

So if I want to run some command while logging off as root, how can I do that ?

---

### Post by Vishal Agarwal on 2010-03-20
Bump

---

### Post by Elfy on 2010-03-20
Not sure why - but I would guess it is associated with the root account being disabled.

Secondly - please do not bump your threads so soon, wait a day then do so.

---

### Post by rnerwein on 2010-03-20
hi
start your command/script as following:
nohup you_stuff
nohup means - ignore SIGHUP ( signal 1 )
ciao

---

