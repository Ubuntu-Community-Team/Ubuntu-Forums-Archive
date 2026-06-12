---
title: "Ubuntu problem!!!!!!!!!!!!!!????????"
date: 2010-01-06
forum: General Help
---

### Post by Adamsom on 2010-01-06
Hi All,

im trying to update some software in ubuntu using the update manager. i type my password in CORRECTLY but then get this error message.
 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.



what does it mean and how do i fix it?

---

### Post by dynamo2 on 2010-01-06
Opening up a Terminal and typing 'sudo dpkg --configure -a' then upgrading should fix it.

---

### Post by SchizmWolf on 2010-01-06
> **dynamo2 said:**
> Opening up a Terminal and typing 'sudo dpkg --configure -a' then upgrading should fix it.

The sudo command should work just fine. A word of advice: if your terminal tells you to do something in order to fix something, it's generally a good idea to do it. It might sound prickish, when put that way, but I'm being totally serious.

---

### Post by howefield on 2010-01-06
> **SchizmWolf said:**
> ..if your terminal tells you to do something in order to fix something, it's generally a good idea to do it. It might sound prickish, when put that way, but I'm being totally serious.

generally ?

Does that mean not always....

---

