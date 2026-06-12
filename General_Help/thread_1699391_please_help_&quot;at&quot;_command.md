---
title: "please help &quot;at&quot; command"
date: 2011-03-03
forum: General Help
---

### Post by gigaferz on 2011-03-03
hello , ive been trying the "at" command for the last couple of days , according to an ubuntu book i got is like a must know command for any admin.

so basically i just want to run the at command in a script.
but before i do that i need to know how to use it. 
as far as i know i need to fix the permissions first in the allow and deny conf files.
in the deny file i deleted bin and the username
then i simply do the following (just a test btw)

sudo at now + 1 minutes
>top
>ctrl+d

i wait for the minute and nothing happens
im logging tru ssh to my ubuntu computer.
now: my goal is to launch a program after a few minutes the system started.
because if i put the program in the start up programs list for any reason it launches but doesnt work.
what am i missing?
any help deeply appreciated.

---

### Post by lykwydchykyn on 2011-03-03
The "at" command seems overkill for just delaying a job for a minute.  Why not write a script like:

```

sleep 60
exec someCommand

```


If you do use "at", then understand that it's going to run any commands in a new (background) shell, not the current shell. Nor will it automatically pop up an Xterm or anything like that.

---

### Post by gigaferz on 2011-03-03
thank you ill try that, well, 
ok, i was specting to see something to pop up
thnks

---

