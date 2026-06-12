---
title: "free shows only 6MB memory free; normal?"
date: 2006-02-22
forum: General Help
---

### Post by ponkan on 2006-02-22
I'm runing Breezy on a laptop with 256 memory (248 after integrated video). I haven't installed any new services, just did the normal install, and executing fee under xterm shows this:
```
             total       used       free     shared    buffers     cached
Mem:        248164     241460       6704          0        656      44252
-/+ buffers/cache:     196552      51612
Swap:       522072      12480     509592

```
Is this amount of free memory normal? It seems that I've been getting a lot more disk thrashing than before, and my system definitely feels more sluggish than when I first installed.

Any help on the matter would be greatly appreciated, thanks

---

### Post by evilgold on 2006-02-22
I'm not positive, but i think that is normal. the only computer i have with 256m ram reports that it has 4mb's free (when a few web pages where open). What i would reccomend for you if your system feels slow, is to use a different (lighter) desktop enviornment. From what i've seen gnome is the 'heaviest' desktop enviorment to run. You could try KDE, or the even ligter XFCE...or just use a window manager like IceWM. 

When I run free on my laptop with 512 ram, i have less then 200mbs free, even when nothings running. Gnome seems to be a bit bulky, I wouldnt use it on a system with any less them 256mbs of ram...if that.

---

### Post by loupy on 2006-02-22
That's normal. You're actually using 196MB - the rest is cached which is normal for linux.  It keeps as much cached memory as possible to run things faster, unlike M$ which (attempts) to release memory every time an app is closed.

---

### Post by az on 2006-02-22
Unused ram is wasted ram.  The linux kernel is aggressive in filling ram.  Don't worry -   it will be dumped when the need arises.

---

### Post by yanik on 2006-02-22
Here's a good introduction on how linux manage memory

[http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html](http://virtualthreads.blogspot.com/2006/02/understanding-memory-usage-on-linux.html)

---

### Post by ponkan on 2006-02-22
Got it. Thanks for the info!

---

### Post by mcduck on 2006-03-19
[QUOTE=ponkan]Got it. Thanks for the info![/QUOTE]
the -/+ buffers/cache line tells how much you have RAM available for programs and how much they use without buffers and disk cache :)

You can also try 'free -m' to get easier to read output.

---

