---
title: "dependency in init.d scripts"
date: 2010-05-29
forum: General Help
---

### Post by nima_a on 2010-05-29
Hi,
is there any way to apply dependency (order) to the execution of init.d scripts ?
I wrote a script and put it in init.d folder and then executed the relative update-rc.d command, but the problem is that the command fails executing on boot time, but it executes with no problem manually. I found that it requires another service (mysql) which I guess it's not ready in time which the scripts starts. 
any ideas ?

---

### Post by nima_a on 2010-05-29
oops, I'm so sorry for bothering , I've just found the options after update-rc.d, working on it ...
so, sorry , and apologize for asking a question without searching **enough**...  ;)
I wish I could delete this topic !

---

