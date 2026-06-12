---
title: "stupid question - return to # in terminal"
date: 2010-05-19
forum: General Help
---

### Post by mcclunyboy on 2010-05-19
Hi,

after i start a process in terminal and you lose the # how do i get it back without quiting the process?

---

### Post by sedawk on 2010-05-19
Press Ctrl-z to pause the foreground process and get
back the prompt.
Now tell the system to continue the paused process
by entering "bg" on the command line.

If you want to move the background process to the
foreground again (e.g. so you can see some output
or to simply press Ctrl-c to stop it) you
simple can enter "fg"

---

### Post by ba_saish on 2010-05-20
you can start the process in background by appending a & at teh end of the command, 
for eg : 

firefox & 

this will return you the pid for the process and return your prompt back. you can use the pid later to kill the process.

---

### Post by Nythain on 2010-05-20
and as a side note, you can also use

ps aux | grep "<part of application name>"
or
pidof <application name>

to also retrieve the pid, in case you forget it or never knew it to begin with :)

---

### Post by dcstar on 2010-05-20
> **ba_saish said:**
> you can start the process in background by appending a & at teh end of the command, 
for eg : 

```
firefox &
``` 

this will return you the pid for the process and return your prompt back. you can use the pid later to kill the process.

and if you want to leave the process running after you close the terminal:

```
process-name & nohup
```

---

