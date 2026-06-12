---
title: "why are there two identical users?"
date: 2010-05-27
forum: General Help
---

### Post by Mark_Galeck on 2010-05-27
Hello, I just installed Ubuntu. When I log in and open a terminal, I see

mark@ubuntu:~$ users
mark mark
mark@ubuntu:~$ uptime
 17:35:04 up 13 min,  2 users,  load average: 0.14, 0.20, 0.14
mark@ubuntu:~$ 


Why is there not just one "mark" but two??

Thank you, 

Mark

---

### Post by jerenept on 2010-05-27
I do not Know, entering the realm of guesswork here.
Maybe the two users have different User ID numbers (UID)?

---

### Post by lisati on 2010-05-27
I remember a similar question being asked in the forums some time back. Apparently it has something to do with a user being able to have more than one "session": once for your terminal session and once for your GUI. [citation needed]

---

### Post by jerome1232 on 2010-05-27
It's because each terminal you open is a new login of your user. So you have an x session running (one login) and one terminal open (second login)

Open three terminal windows, run those commands again. You'll see what I mean.

---

### Post by lisati on 2010-05-27
> **jerome1232 said:**
> It's because each terminal you open is a new login of your user.

Open three terminal windows, run those commands again. You'll see what I mean.

That's it! :)

---

### Post by sisco311 on 2010-05-27
> **Mark_Galeck said:**
> Hello, I just installed Ubuntu. When I log in and open a terminal, I see

mark@ubuntu:~$ users
mark mark
mark@ubuntu:~$ uptime
 17:35:04 up 13 min,  2 users,  load average: 0.14, 0.20, 0.14
mark@ubuntu:~$ 


Why is there not just one "mark" but two??

Thank you, 

Mark

```
who
```

You are logged on twice. 

[tty]("http://en.wikipedia.org/wiki/Data_terminal")**Y** = X server (GUI) 
pts/**X** = [pseudo terminal]("http://en.wikipedia.org/wiki/Pseudo_terminal") (terminal)

EDIT: d'oh, i'm slow!!!

---

### Post by Mark_Galeck on 2010-05-27
the reason why I ask, is because, the "batch" command does not always appear to work, and the man page says, that it is not reliable if there are "competing users".  So I thought, well I seem to have two users...

---

### Post by dcstar on 2010-05-27
> **Mark_Galeck said:**
> the reason why I ask, is because, the "batch" command does not always appear to work, and the man page says, that it is not reliable if there are "competing users".  So I thought, well I seem to have two users...

It also says that batch only runs when system load is below 1.5, so why are you using it?

---

### Post by Mark_Galeck on 2010-05-27
[QUOTE=sisco311;9371079]```
who
```You are logged on twice. 

[]("http://en.wikipedia.org/wiki/Data_terminal")Yes, indeed, I guess, once to the Ubuntu GUI, and the other to the terminal, implicitly I guess?



mark@ubuntu:~$ who
mark     tty7         2010-05-27 17:30 (:0)
mark     pts/0        2010-05-27 20:54 (:0.0)

---

### Post by Mark_Galeck on 2010-05-27
> **dcstar said:**
> It also says that batch only runs when system load is below 1.5, so why are you using it?

I wanted to understand the batch command. I try to run it, but it only works sometimes, and sometimes does not.  I read the man page carefully, found that "is not suitable when users are competing for resources", and reasoned that perhaps that is the case, since in the terminal, when I run batch, there appear to be two users.  So I wanted to understand why there would be two users anyway.

---

