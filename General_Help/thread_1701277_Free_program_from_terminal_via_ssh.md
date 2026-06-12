---
title: "Free program from terminal via ssh"
date: 2011-03-06
forum: General Help
---

### Post by john1923 on 2011-03-06
I am running a program on a "supercomputer" in my department via ssh.

The program is currently giving a progress output to my terminal. 

I want to close my terminal, and log off, without stopping the program on the remote computer. 

I have tried typing & and pressing enter but that didn't do anything.

I'm tempted to just close the terminal, but the program has been running for 2 days (I gave it a lot of data to crunch) and I don't want to lose these last 2 days of work. 

I apologize for the very dumb question.

Thankyou

---

### Post by john1923 on 2011-03-06
If it helps, my terminal runs BASH and the remote machine uses TCSH

---

### Post by Old_Grey_Wolf on 2011-03-06
Bad advice deleted by author.

---

### Post by peculiar penguin on 2011-03-06
You may or may not be able to background (Ctrl-Z, then enter "bg") and detach the process ("disown -h %[jobid]" when using bash, you'll have to look up the tcsh job control syntax). In the future just use screen for tasks like this.

---

### Post by nothingspecial on 2011-03-06
Use screen in future

start screen then your program then press Ctrl-A D to detach it.

then you can log out and leave it running

next time you log on type

```
screen -r
```

You can send a job to the background but if you logout it will kill it.

You might be able to somehow save the process to a file then resume it inside screen but I wouldn't know how.

---

