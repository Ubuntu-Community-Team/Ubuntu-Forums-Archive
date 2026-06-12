---
title: "How to get IO time from /proc/diskstats?"
date: 2010-10-28
forum: General Help
---

### Post by kirium_k on 2010-10-28
I want to know how much time the computer is performing IO read/write during a time interval, so that i can compute the percentage of time spending on IO. I look at /proc/diskstats, and notice that there are these fields:
Field 1 -- # of reads issued
Field 2 -- # of reads merged, field 6 -- # of writes merged
Field 3 -- # of sectors read
Field 4 -- # of milliseconds spent reading
Field 5 -- # of writes completed
Field 7 -- # of sectors written
Field 8 -- # of milliseconds spent writing
Field 9 -- # of I/Os currently in progress
Field 10 -- # of milliseconds spent doing I/Os
Field 11 -- weighted # of milliseconds spent doing I/Os

I thought what I'm interested in are Field 4 and Field 8. However, when I do two readings of /proc/diskstats I got the following results:
   8    0 sda 12536685 8816822 296048322 146032816 7131406 11263533 147237745 1413507864 2 76186068 1559652156
   8    0 sda 12536769 8816838 296060898 146035540 7131406 11263533 147237745 1413507864 2 76187068 1559654872
The second reading is taken 1 second after the first reading. Then the total disk read and write time should be (146035540 - 146032816) + (1413507864 - 1413507864) = 2724 millisecond, which is larger than the time interval between these two readings.
How can this happen? I thought the maximum value of the read and write time should not exceed the total time. Am I doing something wrong? Are there any other methods to get the disk IO time?
Thank you!!!!!

---

### Post by kirium_k on 2010-11-02
I'm still waiting for the answer to this problem, so I have to bring this thread up again /(-_-)\
Hope that somebody here can answer this question! Thank you!

---

