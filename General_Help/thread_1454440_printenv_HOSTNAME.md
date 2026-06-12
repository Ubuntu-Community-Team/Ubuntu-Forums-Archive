---
title: "printenv HOSTNAME"
date: 2010-04-14
forum: General Help
---

### Post by 666f6f on 2010-04-14
Hello all,

I just noticed that ```
printenv HOSTNAME
``` returns nothing while ```
echo $HOSTNAME
``` returns my hostname. 

In the [bash man page]("http://linux.die.net/man/1/bash") it says that the HOSTNAME and other variables are set by the shell. printenv util does not list them all. 

My question is which variables does the printenv util list?

Thank you!

---

### Post by gmargo on 2010-04-14
"Shell Variables" like "HOSTNAME" and "PATH" may or may not be marked for "export" to the environment of subsequently executed commands. In this case, HOSTNAME is not so marked, while PATH is.  The "printenv" tool will only print variables that have been exported.

compare:
```

$ printenv | grep HOST

$ export HOSTNAME

$ printenv | grep HOST
HOSTNAME=tesla

$ export -n HOSTNAME

$ printenv | grep HOST


```

---

### Post by 666f6f on 2010-04-14
gmargo, you :guitar:. Thank you!

---

