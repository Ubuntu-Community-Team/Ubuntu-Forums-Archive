---
title: "find which program is using the internet"
date: 2010-01-27
forum: General Help
---

### Post by rahilm on 2010-01-27
i find some mysterious internet usage on my computer. how can i find out which program is downloading it so that i can pause it and do my work?

---

### Post by t4thfavor on 2010-01-27
ntop is a good one for that I hear. I have never used it, but that is what it's for.

---

### Post by alwayshere on 2010-01-27
put "netstat" in terminal

---

### Post by t4thfavor on 2010-01-28
That doesn't tell you what programs are accessing the network, just where they are pointing. ntop actually tells you the applications that are actively transmitting data.

---

### Post by rahilm on 2010-01-28
i install ntop, but could not make anything out of the output.. does it prompt for passwords?

---

### Post by rahilm on 2010-01-28
this is the output when i run ntop:
```
Thu Jan 28 11:23:46 2010  NOTE: Interface merge enabled by default
Thu Jan 28 11:23:46 2010  Initializing gdbm databases
Thu Jan 28 11:23:46 2010  **ERROR** ....open of /var/lib/ntop/prefsCache.db failed: File open error
Thu Jan 28 11:23:46 2010  Possible solution: please use '-P <directory>'
Thu Jan 28 11:23:46 2010  **FATAL_ERROR** GDBM open failed, ntop shutting down...
Thu Jan 28 11:23:46 2010  CLEANUP[t3077514944]: ntop caught signal 2
Thu Jan 28 11:23:46 2010  THREADMGMT[t3077514944]: ntop RUNSTATE: SHUTDOWN(7)
Thu Jan 28 11:23:46 2010  CLEANUP[t3077514944] catching thread is unknown
Thu Jan 28 11:23:46 2010  CLEANUP: Running threads
Thu Jan 28 11:23:46 2010  CLEANUP: Locking purge mutex (may block for a little while)
Thu Jan 28 11:23:46 2010  CLEANUP: Locked purge mutex, continuing shutdown
Thu Jan 28 11:23:46 2010  CLEANUP: Continues
Thu Jan 28 11:23:46 2010  PLUGIN_TERM: Unloading plugins (if any)
Thu Jan 28 11:23:46 2010  CLEANUP: Clean up complete
Thu Jan 28 11:23:46 2010  THREADMGMT[t3077514944]: ntop RUNSTATE: TERM(8)
Thu Jan 28 11:23:46 2010  ===================================
Thu Jan 28 11:23:46 2010          ntop is shutdown...        
Thu Jan 28 11:23:46 2010  ===================================

```

---

### Post by rahilm on 2010-01-31
ok...i got ntop to work.. but i don't know how to use it..
how to find out which program is using the internet?

---

### Post by rahilm on 2010-02-03
let's say i have deluge downloading files..
how can i see that deluge is accessing the network in ntop??

---

### Post by rnerwein on 2010-02-03
> **t4thfavor said:**
> That doesn't tell you what programs are accessing the network, just where they are pointing. ntop actually tells you the applications that are actively transmitting data.
hi 
oh yes --> netstat will tell you who is using the internet:
run: netstat -t -u -a -p

ciao
:D

---

### Post by t4thfavor on 2010-02-03
Thats a new one for me, I guess I should read the manual more. I suggested ntop, because I figured it would be better ar graphically representing the data.

+1 to netstat -t -u -a -p


But in case you care, to use ntop, start it, and then load the browser and put in

localhost:3000 you will see a webpage with tons of usage information this can be setup to be cumulative, and tell you how much you have used for a certain purpose.

---

### Post by rahilm on 2010-02-05
ya.. netstat shows the network traffic..cool.
```
netstat -t -u -a -p
``` combined with ```
ps -A
```i can know the applications that are using the internet.

thnx guys...

---

