---
title: "Amount of users connected in terminal prompt??"
date: 2006-02-06
forum: General Help
---

### Post by riwa on 2006-02-06
How can i set the amount of users connected to my computer in my terminal prompt?? I've tried stuff like *users | wc* and *who | wc* without success...

Regards
Richard

---

### Post by kabus on 2006-02-06
You mean as part of your prompt ?
Try including 

```
\$(users | wc -w)
```

in your PS1 variable (not sure if this is the best way to do it, though).

---

### Post by riwa on 2006-02-06
Nope. Didn't work. And yes what I want is the number of connected users in my prompt like: 3$ or whatever....

---

### Post by kabus on 2006-02-06
```
[felix@arch ~]$ echo $PS1
\[\033[37m\][\u@\h \W]$\[\033[0m\]
[felix@arch ~]$ PS1="\[\033[37m\][\u@\h \W][users \$(users | wc -w)]$\[\033[0m\]"
[felix@arch ~][users 7]$
```

works for me...:confused:

---

### Post by riwa on 2006-02-06
Sorry. My mistake. I used single quotes and the command itself got printed... Thanks for the help!!

Well ALMOST works like it should except for the fact that it tells me that I'm logged in three times at the same time... How come?

---

### Post by quonsar on 2006-02-06
related question: why am i always logged in twice???

> quonsar@meepzorp:~$ users | wc -w
2
quonsar@meepzorp:~$ users
quonsar quonsar


---

### Post by riwa on 2006-02-06
I get the following message:

[I]
3$ who
riwa     :0           Feb  6 11:17
riwa     pts/0        Feb  6 12:21 (:0.0)
riwa     pts/1        Feb  6 12:22 (:0.0)[/I]

---

### Post by dcstar on 2006-02-06
[QUOTE=quonsar]related question: why am i always logged in twice???[/QUOTE]
The X-session counts as one, the terminal you run the "who" command counts as another one.

---

