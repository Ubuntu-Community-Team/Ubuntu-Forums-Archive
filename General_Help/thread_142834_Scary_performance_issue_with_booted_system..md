---
title: "Scary performance issue with booted system."
date: 2006-03-11
forum: General Help
---

### Post by erjohan on 2006-03-11
I own an X40 Thinkpad and it a really nice machine, I have had no problems with its speed it feels rather snappy most of the time. But this sentiment changed when I tried to search in a 20MB text file: "grep testing /corpus", and it took me 3 seconds to complete the search. Now if you do the math that's 6MB/s which is very slow... 


So I tried alot of things but in the end the only thing that solved it was booting the computer in runlevel 1 with basically nothing loaded. And I searched it in 0.02s or 0.03s, which is quite a speed increase. Lets do that math again, that atleast  600MB/s or 800MB/s.

100x times faster with out anything (services/modules) loaded...

I've tried to limit the system alot, but haven't really managed to find out what it's I'm loading that is causing this. Can you guys give me some hint? This really scares me.

Running Ubuntu 5.10 dist-upgraded from 04.

---

### Post by erjohan on 2006-03-11
Correction I start with init=/bin/bash not runlevel 1, when I start powerowd it takes minimum 0.04s to search it but that is ok.

---

### Post by erjohan on 2006-03-11
1. if I use grep in a script that is run from init  it works, i will get 0.2s in search times (it is running continuously in the background)

2. but while that script is working I can't do the same from the commandline, there I get the same old 3 second search time....

So what is happening why do I get this perfomance issue...

---

