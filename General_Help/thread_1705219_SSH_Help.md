---
title: "SSH Help"
date: 2011-03-11
forum: General Help
---

### Post by aflyingturtle on 2011-03-11
I'm ssh'ing into an ubuntu computer from my ipod to try and remote admin the minecraft server which is the main process of the ubuntu computer. However, I can't find out how to foreground this as the main operation as the sshing ipod. Likewise, If i start the process on the ipod, I can't find out how to foreground it from the terminal. Any way how?

---

### Post by markeee on 2011-03-11
what do you mean how to foreground it?!

---

### Post by oracle2b on 2011-03-11
I think you can place the '&' after the command.

e.g. > vlc &

---

### Post by aflyingturtle on 2011-03-11
> **markeee said:**
> what do you mean how to foreground it?!
Like if you start an application with & it'll run it in terminal background. To foreground it you do fg (job ID). I was wondering how to access the different jobs across the two platforms.

---

### Post by rcorbish on 2011-03-12
Not sure if this helps but...

**jobs** will list all background jobs
then **fg 1** (or whatever) will bring that job to foreground

---

### Post by aflyingturtle on 2011-03-12
> **rcorbish said:**
> Not sure if this helps but...

**jobs** will list all background jobs
then **fg 1** (or whatever) will bring that job to foreground

Sorta... I want to start a proccess A on machine 1. Then use machine 2 to SSH into machine 1 and access process A.

---

