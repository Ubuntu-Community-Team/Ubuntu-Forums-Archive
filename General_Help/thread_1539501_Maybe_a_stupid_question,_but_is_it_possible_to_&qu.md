---
title: "Maybe a stupid question, but is it possible to &quot;assign&quot; a program to a core?"
date: 2010-07-26
forum: General Help
---

### Post by Vunutus on 2010-07-26
Obviously I don't know that much about CPU architecture. 

I have a fancy new quad core CPU in the machine I just built. Now, given the current state of technology, two or many times three of those cores are pretty much sitting idle.

My question is: Is there any way to utilize those extra cores with programs not optimized to take advantage of them? If I have some CPU intensive application, is there any way to tell it to utilize a core that's idling instead of the first core that's probably already got a bunch of processes running on it?

---

### Post by 3Miro on 2010-07-26
What you are describing is exactly how the system works already. If you have one large task/program that can utilize only one core, it will take over on the cores and stay there, while all the other tasks will work on the three "idle" cores. If you are not doing much at the same time, the three other cores will be close to idle.

---

### Post by nmaster on 2010-07-26
there isn't any reason to try and manually set the core anyway.  if you had multiple sockets, then you could use numactl to pin a process to a particular node, but within one processor it doesn't really make much sense. if you're righting multi-threaded code, i'd say just let the OS deal with the scheduling.

there are C functions that deal with this sort of thing though. here is just something i found quickly, i don't think it does what you want
[http://linux.die.net/man/2/sched_setaffinity](http://linux.die.net/man/2/sched_setaffinity)

---

### Post by Vunutus on 2010-07-26
> **3Miro said:**
> What you are describing is exactly how the system works already. If you have one large task/program that can utilize only one core, it will take over on the cores and stay there, while all the other tasks will work on the three "idle" cores. If you are not doing much at the same time, the three other cores will be close to idle.

Is that behavior at the CPU level or is it something handled by the Linux kernel? Like I said I don't know much about CPUs, I just hear over and over about how having more than two cores is a waste since supposedly the others rarely get used. Is that just misinformation or what?

---

### Post by nmaster on 2010-07-26
> **Vunutus said:**
> Is that behavior at the CPU level or is it something handled by the Linux kernel? Like I said I don't know much about CPUs, I just hear over and over about how having more than two cores is a waste since supposedly the others rarely get used. Is that just misinformation or what?

having two cores (unless you have hyper-threading) means that you can run two concurrent threads at one time.  most consumer applications will not use more than two threads, if there is any parallelism at all.  however, multiple cores means that even if one program only used one core, another program could use the other core.  

here's an interesting essay by David Patterson (UC Berkeley EECS) is you'd like to know more about the big picture: [http://spectrum.ieee.org/computing/software/the-trouble-with-multicore/0](http://spectrum.ieee.org/computing/software/the-trouble-with-multicore/0)

---

### Post by -kg- on 2010-07-26
If you are just looking for something to utilize all your cores efficiently, you might want to look into doing some [BOINC Distributed Computing]("http://boinc.berkeley.edu/") projects.  I do SETI@Home currently on my duo-core laptop, and it will do these projects 2 at a time, 1 on each core.  On a quad-core system, it will do 4 work units simultaneously.

There are many deserving apps available, like [Rosetta]("http://boinc.bakerlab.org/rosetta/"):

> Rosetta@home needs your help to determine the 3-dimensional shapes of proteins in research that may ultimately lead to finding cures for some major human diseases.

There are many other projects, and they will all use idle time on your processor to calculate whatever it is they handle.  Just a suggestion, if you wish to absolutely use your processor to its maximum effect.

The BOINC client is available in Synaptic and in Software Center.  Install the BOINC Client and BOINC Manager, then go to the [BOINC Website]("http://boinc.berkeley.edu/") and select the project(s) that you would like to contribute your computing time to.

---

### Post by MaxIBoy on 2010-07-26
```
sudo apt-get install schedtool
```
However, the Linux kernel does a pretty good job of scheduling your processes for you. You should resist the urge to micromanage it, you'll probably just make everything slower.

---

### Post by 3Miro on 2010-07-27
> **Vunutus said:**
> Is that behavior at the CPU level or is it something handled by the Linux kernel? Like I said I don't know much about CPUs, I just hear over and over about how having more than two cores is a waste since supposedly the others rarely get used. Is that just misinformation or what?

This is done at the level of the Linux kernel. If you have only one core, everything will run on it. If you have two or more, then you can still get added benefits, since every system always runs many different processes all at the same time. Basically if you have two cores and one big single thread application, then the app will run on one core and everything else on the other, this will make things go a little bit smoother.

More and more current apps start taking advantage of multi core architecture. I would say that right now there is definite advantage for two cores and more in the future. Even right now, many of the latest games and apps will take full advantage of as many cores as you have.

---

