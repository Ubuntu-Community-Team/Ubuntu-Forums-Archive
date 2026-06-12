---
title: "memory statistics which is correct ?"
date: 2009-12-18
forum: General Help
---

### Post by chuina on 2009-12-18
At the same time, 

```
chuina@desktop:~$ free 
             total       used       free     shared    buffers     cached
Mem:        767672     750108      17564          0      52560     472508
-/+ buffers/cache:     225040     542632
Swap:      2000052          0    2000052

```and 

```
chuina@desktop:~$ vmstat 
procs -----------memory---------- ---swap-- -----io---- -system-- ----cpu----
 r  b   swpd   free   buff  cache   si   so    bi    bo   in   cs us sy id wa
 3  0      0  17564  52560 472508    0    0   101    58  267  625 26  4 68  1
```and [IMG]http://ubuntuforums.org/home/chuina/Desktop/memstat.jpg[/IMG]

and  System>Administration>System Monitor shows : ```
230.5 MiB (30%) of 749.7 MiB
```(I didn't find anything to upload photo from my pc)

Why first free,vmstat giving one reading and System Monitor is showing another ?
Which one is showing the correct memory status ? 
Please tell me, cause if the system use more than 50% of its memory,
Then i'll add few more memory.

Thanks.

---

### Post by northern lights on 2009-12-18
*free*:
* used (used by apps + buffers + cached): 750108KB (225040KB + 52560KB + 472508KB)


*System Monitor*:
230.5 MiB of 749.7 MiB (used by apps of total)


Same stat.
Plausible?

---

### Post by audiomick on 2009-12-18
Hi.
I am not too sure on this, but I read something recently on the subject.

It seems that some tools for showing memory statistics take into account memory resvered for system functions, and show it as occupied, and some don't. I am sorry, but I don't know which is what.

Anyway, I would be inclined to believe whichever is showing the highest usage. If you can afford to stick some more RAM in, it never hurts...:)

Bear in mind that you might want to expand your swap partition accordingly if you want the suspend / hibernate functions to work properly. For that, your swap needs to be at least as big as your RAM.

---

### Post by lisati on 2009-12-18
> **chuina said:**
> (I didn't find anything to upload photo from my pc)


On Applications->Accessories there's "Take Screen shot"

Down the forum page a bit is "Manage attachments"

---

### Post by chuina on 2009-12-19
thanks northern lights and others,
its my mistake to read them.

sometime changing hardware causes
issue in non-brand pc , thats why i post that.

---

### Post by lukeiamyourfather on 2009-12-19
I think htop shows the relationship the best between the used memory and buffer cache. Everything the system reads from or writes to the disk is kept in the memory in case something needs it again, this is the buffer cache. If an application needs memory then the oldest item in the buffer cache is let go to free memory. So what you should really be concerned with is what the applications are using instead of the total including the buffer cache.

Install htop with this in the terminal.

```
sudo apt-get install htop
```

Then run it when you get it install using the same command in a terminal. You should see something like the attached image. The green in the memory bar shows the memory is used by applications, the blue is reserved memory for whatever system purposes, and the yellow is the buffer cache. The number on the left is how much is used by applications, the left is how much memory the system has. So in my case the whole 16GB in the system is used, 11GB are used by applications, a little by the system for background things, and the rest of the 5GB is a buffer cache. So I still have 5GB more room for applications even though some other tools say the memory is completely used up. 

When booting up you'll probably have no buffer cache at all since nothing is read from or written to the disk at that point. Long story short don't worry about the memory being used from the buffer cache because it only speeds things up and will free up when an application requests it. Cheers!

---

