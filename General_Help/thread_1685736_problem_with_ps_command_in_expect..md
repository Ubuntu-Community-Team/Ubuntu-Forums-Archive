---
title: "problem with ps command in expect."
date: 2011-02-11
forum: General Help
---

### Post by vardhanReddy on 2011-02-11
Hi Friends,

                     I am Vardham,   i am learning expect script, can any one tell me how to set the following commands out put in a variable.

   
                 send -- "ps -e | grep a.out | awk \'{print \$1}\' \n"

i want to set the pid value returned by the above command in a variable. 


Regards,
Vardhan Reddy.

---

### Post by anglican on 2011-02-11
> **vardhanReddy said:**
> Hi Friends,

                     I am Vardham,   i am learning expect script, can any one tell me how to set the following commands out put in a variable.

   
                 send -- "ps -e | grep a.out | awk \'{print \$1}\' \n"

i want to set the pid value returned by the above command in a variable. 


Regards,
Vardhan Reddy.To get a PID that is hugely over-complex, "ps" will do the whole job for you:
```
ps -C a.out -o pid=
```to set this in a variable:
```
SOME_VARIABLE=`ps -C a.out -o pid=`
```

H

---

