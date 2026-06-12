---
title: "Ubuntu 10.04.1 dont boot in graphics mode"
date: 2011-02-04
forum: General Help
---

### Post by panachippara on 2011-02-04
I had been using Ubuntu 10.04.1 in a Macbook pro (triple boot: Mac, Win7 and Ubuntu). Now I am not able to boot in to Ubuntu in graphics mode. It just freezes after the Ubuntu logo appears. It happened once before and I re-installed the OS. Now I have the same issue. I can boot in recovery mode and get into my account. When I tried startx command I get the error below

xinit: connection refused (error 111) unable to connect to xserver
xauth:error in locking authority file /home/joy/.xauthority

(there is more stuff splashed on the screen, but the above two are the only errors I see)

Please help. I thought of reinstalling the OS. But this may happen again and re-installing the OS every month wipes out all my configurations and files in my account.

---

### Post by TeoBigusGeekus on 2011-02-04
Delete the offending file
```
rm ~/.xauthority
```
and try again
```
startx
```

---

### Post by panachippara on 2011-02-04
> **TeoBigusGeekus said:**
> Delete the offending file
```
rm ~/.xauthority
```and try again
```
startx
```

Many thanks for the reply.

I tried 
```
rm ~/.xauthority
```and got error message that no such file or directory

tried 

```
ls -a /home/joy/
```and did not see any files named .xauthority

looks strange. What to do next?

---

