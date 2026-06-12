---
title: "is the Process scheduler a part of  Process queue"
date: 2010-08-12
forum: General Help
---

### Post by anirudhtomer on 2010-08-12
hello everyone,

as we all know Process Scheduler does Process scheduling and its a process as well.
I was just wondering that if this happens then the Process "Process Scheduler" should be a 
part of Process queue as well. 

So if there are 5 process are there in Process queue & process scheduler is administrating them then since its also a process, once it puts a process under RUN state it should itself go inside queue because at one instant only one process can get executed on a processor.

This is quite confusing for me. Please help me out. 

I tried to search on this but could not find any relevant topics.
Thanks in advance

---

### Post by anirudhtomer on 2010-08-12
Isn't there anyone who knows how a process scheduler is working on linux

---

### Post by dino99 on 2010-08-12
maybe i dont understand what you mean, but:

- there is no circular state in the queue (fifo or uid priority)
- a proc with multithreads is able to run several process if the app allow it

---

### Post by anirudhtomer on 2010-08-12
I wanted to say that

lets assume there are 3 process running +  1 process scheduler (which is also a process)
& while the process scheduler is running (to determine which process to be executed on the next clock) other processed are in READY STATE.

now as soon as next clock cycle comes say process1 is given the chance & it comes under RUN state. since at a time only one process can reside in RUN state on a single processor system like P4 other processes must still be in a queue....and since PROCESS SCHEDULER IS ALSO A PROCESS...it should as well be in READY STATE rather than being in RUN state.
so that's what the question is...am I thinking in right direction or not?

& if I am thinking right then who makes the PROCESS SCHEDULER come back to RUN state.

& I am going wrong then please show me the right direction.
I would be thankful to have a reply

---

### Post by dino99 on 2010-08-12
this is something that kernel devs can explain better than myself, but as said previously each process get is own priority given by the kernel or by the app if its dev want to bypass the generic priority (not so easy because of objets programming and their dependencies)

if your question mean you are developing and wonder about schedeler, you may want to post your question on launchpad (QA), there dev will give you a tecnical point of view or link to study

[https://answers.launchpad.net/ubuntu](https://answers.launchpad.net/ubuntu)

**** on top right side: ask a question  *****

---

### Post by anirudhtomer on 2010-08-12
thanks for telling me the link of that site. Hopefully I will get a reply there.
I will wait for people to help me out on this issue at this forum.

---

