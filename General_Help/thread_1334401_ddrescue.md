---
title: "ddrescue"
date: 2009-11-22
forum: General Help
---

### Post by gypsumwolf on 2009-11-22
I am trying to image a HDD to rescue files. The hard drive sounds like it is doing something but there is not change from the output on the screen. The output is:

```
root@voyager:~# ddrescue -v /dev/sdc /home/wolf/foremost/image /home/wolf/recovery/out


About to copy 40020 MBytes from /dev/sdc to /home/wolf/foremost/image
    Starting positions: infile = 0 B,  outfile = 0 B
    Copy block size: 128 hard blocks
Hard block size: 512  bytes
Max_retries: 0    
Direct: no    Sparse: no    Split: yes    Truncate: no

Press Ctrl-C to interrupt
Initial status (read from logfile)
rescued:   665453 kB,  errsize:    657 kB,  errors:       4
Current status
rescued:   665519 kB,  errsize:    657 kB,  current rate:    66048 B/s
   ipos:   666177 kB,   errors:       4,    average rate:    66048 B/s
   opos:   666177 kB,     time from last successful read:       0 s
Copying non-tried blocks...

```

How do I know when its done or if it really is doing anything?

---

### Post by gypsumwolf on 2009-11-22
Bump

---

### Post by gypsumwolf on 2009-11-23
Bumpp. (should the be pasted in a different thread?)

---

