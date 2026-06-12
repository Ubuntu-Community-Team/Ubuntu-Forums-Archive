---
title: "how to disable access to running processes for some user"
date: 2010-01-09
forum: General Help
---

### Post by buratinas on 2010-01-09
Hello,

is there any possible way to hide currently running processes from an user? This means I do not want him to know about what programs/processes does any other user but him run.

In short words if that user runs 'ps -aux' he should get only his processes.

---

### Post by abcuser on 2010-01-09
Hi,
save following command to ~/.bashrc for each user or save to /etc/bash.bashrc for all users.
```
alias ps='ps aux | gawk '\''$1==USERNAME {print}'\'' USERNAME=${USERNAME}'

```

Then user when executes ```
ps
``` command he/she only gets his/hers own processes.

But be careful if user is running some kind of script that is involving ps command it will probably fell.

Also if user executes "alias ps='ps aux' he/she will get whole control of ps command. Of if he/she is using "unalias ps". So there should also be some read/write/execute privileges prevented for users.

This also does not solve the problem if user is using any other tool/command to list processes.

This is just an idea, how good it is depends on what kind of users you have.
Regards

---

### Post by falconindy on 2010-01-09
Going to be pretty difficult to do this, as ps just reads the contents of /proc. Changing permissions on /proc is both futile (recreated every boot) and a bad idea.

Why is it you want to hide processes from other users?

---

### Post by rnerwein on 2010-01-09
hi
if the he/she have a little bit of practice in unix/linux i think it's not possible with a class d (normal not a security) system to hide the processlist - to many possibilities (e.g. /proc ......).
ciao

---

