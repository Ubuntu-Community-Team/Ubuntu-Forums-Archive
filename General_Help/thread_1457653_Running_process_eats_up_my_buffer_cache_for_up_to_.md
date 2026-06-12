---
title: "Running process eats up my buffer cache for up to 20 minutes after run"
date: 2010-04-18
forum: General Help
---

### Post by brian.takita on 2010-04-18
I'm running a pretty heavy-weight process (Rails tests) that involves several worker processes, in an effort to parallelize the runs.

To measure the performance impacts, I run hdparm -T /dev/sda to give me the cached read performance. Note that the disk IO is not being measured, but the disk cache IO is.

It works very well on my work machine (8-core Mac Pro running Ubuntu with 8GB of RAM).

The baseline is:
honk4:~ $ sudo hdparm -T /dev/sda
/dev/sda:
 Timing cached reads:   13224 MB in  2.00 seconds = 6616.86 MB/sec

In the middle of the test run:
honk4:~ $ sudo hdparm -T /dev/sda
/dev/sda:
 Timing cached reads:   4598 MB in  2.00 seconds = 2299.26 MB/sec

After the test run is finished, hdparm returns back to the original result. The test suite ran 8 workers.

---

On my laptop, it is a different story.
I have a quad core machine with 3.4GB of RAM.
The test suite runs 4 workers.

Now the baseline is around 6000 MB/sec.
When I run the suite, it ranges between 2000-5000 MB/sec.
After the suite is finished, the performance keeps on dropping. It finally goes down to ~ 350 MB/sec.

What is strange is around 30 minutes later, hdparm -T goes back to 6000 MB/sec.

I tried sudo sh -c 'sync; echo 3 > /proc/sys/vm/drop_caches', but it does not seem to help.

Does anybody have any recommendations? I'll try to keep the thread posted if I find out anything else.

Thank you,
Brian

---

### Post by brian.takita on 2010-04-18
I have also killed any related processes. When I run ps aux, I do not see any evidence of the processes I was using.

---

### Post by brian.takita on 2010-04-18
Currently, Xorg is eating 90% of my cpu. I'm not sure if is the cause or the symptom of the buffer cache thrashing.

---

