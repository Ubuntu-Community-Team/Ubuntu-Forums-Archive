---
title: "Virtual memory is taking up too much space"
date: 2011-03-08
forum: General Help
---

### Post by Nixxous on 2011-03-08
hi, im wondering if there is anyway to control how much virtual memory is used because it keeps taking up too much disk space when im trying to run a program on my server, all i need is about 5gb spare and it can use the rest but im unsure how to go about it, currently running ubuntu server 10.04
 
any guidence appreciated thanks

---

### Post by lithopsian on 2011-03-08
Most queries get answered very quickly on this forum.  Yours hasn't been answered because it makes little sense.

Are you talking about swap space?  Are you talking about some other form of virtual memory?  What do you mean by needing 5GB spare?  5GB of what and where?  What is using the "virtual memory"?  What are you trying to reserve and why?

Try to formulate the question more clearly and I'm positive someone will have an answer for you very quickly.

---

### Post by Nixxous on 2011-03-09
Oh right, sorry :) ok basically, im running a test game server, but when i start the programs up my hard drive space starts going down, untill it gets to no space on the hard drive at all, then i have to restart the server to gain my space back, so i was under the assumption that it was using my hard drive space for virtual memory, I dont mind it doing this however i need about 5gb spare hard drive space and the amount of space used doesnt go down untill i restart, as im only testing i dont want to shell out for extra memory or hard drive space if there is a way to make it so that it doesnt use that last 5gb of hard drive space, otherwise this project could turn out more expensive than i had hoped.
 
thanks

---

### Post by oldos2er on 2011-03-09
How much RAM do you have? How big did you make swap? 

You can try changing the swappiness value [https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?](https://help.ubuntu.com/community/SwapFaq#What is swappiness and how do I change it?)

---

### Post by jerome1232 on 2011-03-09
Sounds more like an errant temporary file filling up your disc... (like a log or something in /tmp)

Swap is generally on a separate partition or in a swap file which is limited in size so it's filling up won't affect your OS partition.

Perhaps get the disc to fill up and post the output of these commands

```
free -m
sudo df -h --max-depth=1 /
```

---

### Post by lithopsian on 2011-03-09
Agreed.  Not swap.  The game *might* be taking disk space for some form of virtual memory but that's unlikely.  Most likely it is creating files as described.  Let it create some and then try to find out what they are and whether it is a bug or whether it is supposed to do that.

Modern games can be pretty brutal on disk space, so maybe you'll need a bigger disk.

---

