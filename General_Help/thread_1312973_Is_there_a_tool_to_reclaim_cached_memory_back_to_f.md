---
title: "Is there a tool to reclaim cached memory back to free?"
date: 2009-11-03
forum: General Help
---

### Post by lotuseclat79 on 2009-11-03
I am running the Karmic Ubuntu 9.10 Live CD, and when I issue the free command I get:
ubuntu@ubuntu:~/Desktop$ free
             total       used       free     shared    buffers     cached
Mem:       2965804    1666888    1298916          0      96404    1259768
-/+ buffers/cache:     310716    2655088
Swap:      1799228          0    1799228

Is there a tool that can reclaim the cached memory back to the free pool?

For example, if I have already shut down the apps that I was previously running, and do not plan to invoke them again, and require lots of free memory to do the next thing I want to run, how can I ensure the maximum amount of free memory to invoke the maximum amount of free memory and minimum amount of cached?

-- Tom

---

### Post by wildweathel on 2009-11-03
There's no reason to.  If Linux runs out of free memory, it will allocate from cached.  This is maybe a few percent slower than an allocating from free (since it requires a little bit more bookkeeping).  However, if Linux were to preemptively clear cache and a program tries to request cached data it will be much slower, at least a few hundred times slower, to read it from disk.

You want cache.  It's good for you.  Are you experiencing any performance issues?

---

### Post by P4man on 2009-11-03
I think you (OP) are confusing swap and cache. Swap is what you dont want, its when harddisk gets used to store running programs or their data. Moving stuff to and from swap is slooow. Cache is when unused RAM memory is used as read or write buffer to your harddisk. Cache is GOOD.

Now windows has the strange habbit of swapping applications to.. swap very quickly and use the freed ram as more cache. Which is kind of silly in most usage scenario's. Its the reason many windows users tell you to disable swap, so windows no longer can be so silly.

Linux by default swaps very rarely, pretty much only when it needs to (check your own output, you are using zero swap. When was the last time you saw that in windows>). It will still use whatever free ram you have as cache. There is no reason to intervene unless you have very specific requirements.

---

### Post by scouser73 on 2009-11-03
Use Bleachbit

> **sudo apt-get install bleachbit**

---

### Post by lotuseclat79 on 2009-11-03
> **wildweathel said:**
> There's no reason to.  If Linux runs out of free memory, it will allocate from cached.  This is maybe a few percent slower than an allocating from free (since it requires a little bit more bookkeeping).  However, if Linux were to preemptively clear cache and a program tries to request cached data it will be much slower, at least a few hundred times slower, to read it from disk.

You want cache.  It's good for you.  Are you experiencing any performance issues?
Hi wildweathel,

Thanks for the reply, I think that answers my question.  No performance issues.

What I have is 4GB of RAM, and I am attempting to follow the procedure (modified for my Live CD environment w/Karmic) to produce a similar Live CD which uses PAE kernel packages instead of the 9.10 release kernel packages.  I considered remastersys, but the originator of that said I did not have enough RAM though he said I was only the 2nd person whom asked if it was possible to do what I need in the last 3 years and he would look for his notes of that person's effort which was apparently successful (i.e. modified to his requirements similar to mine - still no feedback from him).

In the meantime, I've found the article: [How To: Customize your Ubuntu Live CD](http://www.debutu.org/how-to-customize-your-ubuntu-live-cd/) which seems like just what I need to do (with modifications).

My post was relative to what I noticed and wondered about after this morning's session from running the free and top commands.

Thanks again,

-- Tom

P.S.  I have a felling that such a vanilla PAE Live CD is very much in demand, and when I get there if no one else has one, I plan to put it through the testing mill here or wherever that is done to see if it can be added to the repositories - i.e. it sure would be a lot easier if someone at Ubuntu Central (Canonical) made one available for download! ;)

---

### Post by lotuseclat79 on 2009-11-03
> **P4man said:**
> I think you (OP) are confusing swap and cache. Swap is what you dont want, its when harddisk gets used to store running programs or their data. Moving stuff to and from swap is slooow. Cache is when unused RAM memory is used as read or write buffer to your harddisk. Cache is GOOD.

Now windows has the strange habbit of swapping applications to.. swap very quickly and use the freed ram as more cache. Which is kind of silly in most usage scenario's. Its the reason many windows users tell you to disable swap, so windows no longer can be so silly.

Linux by default swaps very rarely, pretty much only when it needs to (check your own output, you are using zero swap. When was the last time you saw that in windows>). It will still use whatever free ram you have as cache. There is no reason to intervene unless you have very specific requirements.
Hi Prman,

Nope, I've never been confused about the difference between swap and cache, I just did not know that if free memory gets exhausted the  allocator will get it from cache.

See my requirements in my response to wildweathel.

Thanks for your reply,

-- Tom

---

### Post by lotuseclat79 on 2009-11-03
> **scouser73 said:**
> Use Bleachbit
Hi scouser73,

Bleachbit does not meet my requirements.  See my response to wildweathel.

Thanks for the reply.

-- Tom

---

