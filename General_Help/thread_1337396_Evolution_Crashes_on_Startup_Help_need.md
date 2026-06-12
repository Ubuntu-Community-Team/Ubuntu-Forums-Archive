---
title: "Evolution Crashes on Startup Help need"
date: 2009-11-25
forum: General Help
---

### Post by rajesh1136 on 2009-11-25
rajesh@rajesh-desktop:~$ evolution
** (evolution:4104): DEBUG: Loading Exchange MAPI Plugin 

** (evolution:4104): DEBUG: MAPI listener is constructed with 0 listed MAPI accounts 
** (evolution:4104): DEBUG: mailto URL command: evolution %s
** (evolution:4104): DEBUG: mailto URL program: evolution

** (evolution:4104): CRITICAL **: atk_object_set_name: assertion `name != NULL' failed
Segmentation fault
rajesh@rajesh-desktop:~$ 


i tried reinstallation and also complete removal and re installation. still same problem. please help

---

### Post by rajesh1136 on 2009-11-26
i myself solved the problem by starting 

evolution --offline

then it came i removed the accounts and added again.

---

### Post by rajesh1136 on 2009-11-26
i figured the problem. i configured microsoft exchange server in evolution 2.28 and when i set OOO message.

After restarting evolution it crashes

if i start in offline mode and remove OOO message it works correctly.

will report this problem

---

