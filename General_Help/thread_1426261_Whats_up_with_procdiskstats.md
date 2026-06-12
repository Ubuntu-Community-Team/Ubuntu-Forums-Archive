---
title: "Whats up with /proc/diskstats?"
date: 2010-03-10
forum: General Help
---

### Post by manemannen on 2010-03-10
Hello, 

I am trying to understand the figures in /proc/diskstats but I seem to be missing something fundamental.
I wanted to see the read and write times when copying a file from internal NAND to an SDCard on my target device so I did the following. 

I took a snapshot from the /proc/diskstats file for the relevant device (the sdcard). It looked like this:

```
179       0 mmcblk0 2168 7824 180975 29690 1001 12968 185120 550450 0 32440 580130
```

Now, I copied a 30MB file and the whole operation took like 10 seconds to complete. The SDCard is of class 6 and has a max transfer rate of 6MB/s so this seems to be in order including some overhead and such. Now, immediately after the copy I took another snapshot and it looked like this:

```
179       0 mmcblk0 2739 7824 239482 35390 1308 16708 246814 706930 0 41550 742300
```

No, other SDCard activity occurred.

Now to the part I just can't get. According to the iostats.txt in the kernel documentation field 8 (write time per device) is measured in milliseconds.

```
...
77    Field  8 -- # of milliseconds spent writing
78        This is the total number of milliseconds spent by all writes (as
79        measured from __make_request() to end_that_request_last()).
...
```

So, the diff of field 8 between the two snapshots is 156480 milliseconds (~156 seconds) which is a lot more than the clock time between the two snapshots.
Can someone please explain the measured time? It can't be CPU time - so what is it?

(running on a Linux 2.6.29 kernel)

Can someone shed some light on this?
/M

---

### Post by manemannen on 2010-03-11
bump..replying to myself as usual ](*,)

None out there with an answer?

/M

---

