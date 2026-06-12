---
title: "multiple threads all on the same core"
date: 2009-11-27
forum: General Help
---

### Post by Alexander Blackbird on 2009-11-27
Hi! I have Ubuntu 9.10 karmic x64 running on my QuadCore system and I try to run a simple application using multiple threads. It calculates Pi and measures time of calculation. And I found that serial version took approximately as much time as multy-threaded. I tried both using OpenMP and manually creating threads with pthread_create(), but the result was the same, and on the very same machine under MS Windows it showed 4 times speeding-up, as expected. Under Ubuntu 9.10 OpenMP detects 4 cores and spawn 4 threads,  but they just run slowly, and I suspect that all threads are assigned to same CPU core. I ran a few instances of the same application simultaneously, but the speed did not drop, and so it proves that all threads are run on the same core. Does it have something to do with kernel or gcc? What may be the cause of this strange behavior? Thanks in advance  The source code for my application can be found here: [http://dumpz.org/14701/](http://dumpz.org/14701/)

---

### Post by shaggy999 on 2009-11-27
Are you sure time isn't being measured as a summation of the time for all threads completed? I just recently created a multi-threaded bash script that pegged all of my cores @ 100%. The real-time for this execution was about 20 seconds where it was normally 80 seconds (this is on a quad-core system), but the 'time' command that I ran returned actually a longer time (83 seconds) for the multi-threaded version vs single threaded version because it added up the time for all 4 threads and added in the extra overhead for context switching.

Also, this post would be better off in the programming subforum.

---

### Post by Alexander Blackbird on 2009-11-27
> **shaggy999 said:**
> Are you sure time isn't being measured as a summation of the time for all threads completed? 

  Yeah. I am pretty sure. This code is like a "hello  world" from any parallel-programming book and I measured time before and after  parallel part. And I guess anybody can tell 2 seconds from 8 even without any  measurements...
 
> **shaggy999 said:**
> Also, this post would be better off in the programming subforum.

My bad. Maybe the forum administrators will be so kind as  to move this thread to the right subforum...

---

### Post by dcstar on 2009-11-27
> **Alexander Blackbird said:**
> 
........
Under Ubuntu 9.10 OpenMP detects 4 cores and spawn 4 threads,  but they just run slowly, and I suspect that all threads are assigned to same CPU core. I ran a few instances of the same application simultaneously, but the speed did not drop, and so it proves that all threads are run on the same core.
........

Simply use the System Monitor to view the real time usage of each core.

---

### Post by shaggy999 on 2009-11-28
How did you measure time? Did you use the 'time' program or did you just use a stopwatch or something?

---

### Post by Alexander Blackbird on 2009-11-28
Sorry, the problem was really with measuring time - "stopwatch"  method showed correct timings and all cores were utilized. I used **clock()** call to get cpu clock counts and it works strange. I have not yet digged into clock() documentation, but that code was used in Intel tutorials and it worked well on other platforms. It's weird but at least there is no problem with distributing threads. Measuring time with omp_get_wtime() or even with simple time() works well.

---

### Post by shaggy999 on 2009-11-28
> **Alexander Blackbird said:**
> Sorry, the problem was really with measuring time - "stopwatch"  method showed correct timings and all cores were utilized. I used **clock()** call to get cpu clock counts and it works strange. I have not yet digged into clock() documentation, but that code was used in Intel tutorials and it worked well on other platforms. It's weird but at least there is no problem with distributing threads. Measuring time with omp_get_wtime() or even with simple time() works well.

I think that method counts the time from all threads, which is what I mentioned originally.

---

