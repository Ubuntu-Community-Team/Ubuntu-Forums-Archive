---
title: "How to kill aMSN in terminal?"
date: 2011-11-06
forum: General Help
---

### Post by lethalfang on 2011-11-06
```
pgrep amsn
``` doesn't work on amsn!

---

### Post by WorMzy on 2011-11-06
pgrep isn't supposed to kill. Do you mean that it doesn't print a process number?

Try
```
ps aux | grep -i amsn
```

That won't kill either, but it should return a process number, which you can then use with kill.

---

### Post by lethalfang on 2011-11-06
> **WorMzy said:**
> pgrep isn't supposed to kill. Do you mean that it doesn't print a process number?

Try
```
ps aux | grep -i amsn
```

That won't kill either, but it should return a process number, which you can then use with kill.

Yeah, I know that pgrep doesn't kill. It didn't return a process number. 

Your code yields:
1000      3792  0.6  1.2  94224 44100 ?        Sl   13:36   0:20 wish8.5 /usr/bin/amsn
1000      4133  0.0  0.0   2140   732 pts/3    S+   14:32   0:00 grep -i amsn

... I was able to kill aMSN by killing wish. Not sure if there is a more "proper" way than "killall wish."

---

### Post by Comrade7 on 2011-11-09
I usually just go with
> killall program

Don't put the word "program" of course, put the program you wish to kill, such as > killall amsn

---

