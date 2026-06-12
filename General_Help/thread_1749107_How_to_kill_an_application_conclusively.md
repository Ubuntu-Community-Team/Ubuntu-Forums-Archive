---
title: "How to kill an application conclusively?"
date: 2011-05-04
forum: General Help
---

### Post by le1 on 2011-05-04
Hey there,

I'm trying to kill an android SDK emulator but it just won't shut down. When I try to kill it through system monitor (see pics) it doesn't work, "killall program_name" doesn't work either. It stays firm and all I have left is to reboot Ubuntu. Is there any conclusive solution to that ?

---

### Post by stoneage on 2011-05-04
I think the default is kill -15 which tells the application to exit normally. If you need to force it try kill -9

So, for the example you show it would be ```
kill 2331 -9
```

---

### Post by le1 on 2011-05-04
Well, I get:

/$ kill 2331 -9
bash: kill: (-9) - No such process
/$ kill 2331 -15
bash: kill: (-15) - No such process

---

### Post by Hanmac on 2011-05-04
try "sudo killall emulator -KILL"
or use "xkill"

---

### Post by jamesjenner on 2011-05-04
You should be using:

```
kill -9 <process id>
```

Just looked at man and it appears that -9 cannot be blocked. KILL is the same as -9.

The reason why you get the error is because it thinks -9 is a process id, not an option, you need to put it at the start. I suspect it may not have worked because the process you were trying to kill was blocked, switching them around should solve your problem.

No need to use sudo unless its a process not used by your account.

Cheers,

James.

---

### Post by le1 on 2011-05-04
Well, **jamesjenner** you just killed this thread, I mean solved, thanks!

> **jamesjenner said:**
> 
```
kill -9 <process id>
```
**--> In my case:**
 kill -9 2556
&
 kill -9 2331


---

### Post by stoneage on 2011-05-04
Ooops, of course that *is* what I was trying to say.

Sorry for the confusion :D

---

