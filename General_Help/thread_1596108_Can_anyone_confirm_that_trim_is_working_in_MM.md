---
title: "Can anyone confirm that trim is working in MM?"
date: 2010-10-13
forum: General Help
---

### Post by josephellengar on 2010-10-13
... I don't know how.  For anyone who is not familiar with it, I am talking about the trim functionality in the 2.6.33 kernel for solid state drives.

---

### Post by happyhamster on 2010-10-13
Don't know if it's TRIM for sure, but *something* is performing magic on Maverick for SSD performance. When running the System->Administration->Disk Utility->Benchmark (Read-Only Benchmark), results improved considerably compared to previous incarnations. 

30GB OCZ Vertex.

First result (Jaunty, I believe):
Read Rates:
Min 77.2
Max 259.3
Avg 154.3
AT 0.1 ms

Previous result (Maverick alpha/beta release):
Read Rates:
Min 194.3
Max 250.8
Avg 232.2
AT 0.3 ms 
(These figures stayed more or less constant during Maverick's development, which equals ~ 4 months.)

Current (Maverick, custom 2.6.36-rc7 kernel):
Read Rates:
Min 208.1
Max 264.2
Avg 245.0
AT 0.2 ms
(This install is only a few days old.)

---

### Post by josephellengar on 2010-10-13
I can concur.  Intel G2 160 gb x-25m.
My previous install it was about the same speed as my other drive.
(For some reason the old benchmark was erased so I don't have solid numbers)
Now:

Minimum read: 202.4 mb/s
Maximum: 276.3 mb/s
Average: 253.3 mb/s
Average access time: .1 ms

My 320gb 7200 rpm Seagate drive:

Before:
46.9 // 102.7 // 77.7 //16.4ms
Now: 
48.6//103.4//77.2//16.4ms (No significant change on the hdd)

Well, I've only had this kernel installed for a few hours, so I can't say anything about that, except that the performance was definitely closer to the hdd last time I benchmarked the ssd.  I guess I'll report back in a few weeks and see if it has gotten any better.  Because presumably, after years of use, this thing should have a lot to trim.  Anybody else with benchmark results?  I would do a write test as well, but I'm not going to erase the drive just to do that.

---

### Post by happyhamster on 2010-10-14
Lots of benchmarks in this thread:
[http://ubuntuforums.org/showthread.php?t=1468995](http://ubuntuforums.org/showthread.php?t=1468995)

---

### Post by josephellengar on 2010-10-14
> **happyhamster said:**
> Lots of benchmarks in this thread:
[http://ubuntuforums.org/showthread.php?t=1468995](http://ubuntuforums.org/showthread.php?t=1468995)

Yeah, but is everything faster because it's faster or because trim is finally working?

---

### Post by josephellengar on 2010-10-19
Anybody else have information.  Or, in other words, bump.

---

### Post by dcstar on 2010-10-20
> **happyhamster said:**
> Don't know if it's TRIM for sure, but *something* is performing magic on Maverick for SSD performance. When running the System->Administration->Disk Utility->Benchmark (Read-Only Benchmark), results improved considerably compared to previous incarnations. 
.........

My 10.04 SSD benchmarks are similar to the "good" ones, so it has nothing to do with 10.10.

And TRIM has little (if anything) to do with Read performance, it is the ability to optimise Write performance (and increase SSD longevity) that TRIM affects.

Unless you have the discard option in /etc/fstab then real-time TRIM will not function, eg:
```
UUID=adaf9c80-1d4e-40d8-a7f6-171f6523c8e1 / ext4 errors=remount-ro,noatime,nodiratime,**discard** 0 1
```

---

