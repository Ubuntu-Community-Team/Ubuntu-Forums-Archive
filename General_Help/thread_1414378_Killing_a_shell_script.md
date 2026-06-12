---
title: "Killing a shell script?"
date: 2010-02-23
forum: General Help
---

### Post by kizofilax on 2010-02-23
Hi, I have a shell script called odot.ssh and i am looking for a way to kill it from the command line. I cannot use ctrl c because i am writing another script which I will use to kill this odot script.

I have found that kill bash kills this process but I was wondering if there is another way to do it like with the name "kill odot" or somethig like that. 

THanks

---

### Post by r_s on 2010-02-23
using ps you can find the process id *(pid)* for this process and then using kill *pid* or kill -9 *pid* you  can kill that process without hampering any other process.

---

### Post by kizofilax on 2010-02-26
Ok that worked, thanks =)

---

### Post by DaithiF on 2010-02-26
or you can do killall <name>, so for example
```
killall odot.sh

```will match any running processes with odot.sh in their name and kill them

---

