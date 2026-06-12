---
title: "Start-up suddenly extremely slow"
date: 2010-02-10
forum: General Help
---

### Post by sammasaurus on 2010-02-10
I don't think any changes have been made to my laptop, but it suddenly loads Ubuntu extremely slowly.  The time it takes to get from the Toshiba boot screen to the Ubuntu Log-in screen takes easily 20x as long.  

Has anyone else been experiencing this kind of lag or have any ideas where to begin?



[sorry if this is a repost, but the post I made two days ago ... vanished.  or was deleted for some reason?]

---

### Post by RedSingularity on 2010-02-10
What screen does it seem to be hanging at?

---

### Post by sammasaurus on 2010-02-10
My Toshiba boot screen moves at normal pace; once it disappears, however, the black screen with a white Ubuntu logo hangs, as well as the brown Ubuntu log-in loading screen. Additionally, between all 3 screens, the wait-wheel appears and spins away for some 15 seconds.  

No one screen seems to have a longer lag than another.

My computer also seems fine once I've fully logged in.

---

### Post by RedSingularity on 2010-02-10
How old is your HDD?

---

### Post by sammasaurus on 2010-02-10
Purchased my comp Fall 2006, so 3.5 yrs?  And would it be typical for a HDD's failure to only affect boot time at first?

---

### Post by RedSingularity on 2010-02-10
Well usually it would effect the working of the system even when its being used normally.  I have had cases though where the boot is EXCRUCIATINGLY slow and the computer has worked fine after boot.  This sounds like what your experiencing.

---

### Post by adam814 on 2010-02-10
I have a few questions that might narrow down potential problems for you:

1) Did you install using wubi?  If so it might benefit you to defragment your Windows drive as excessive fragmentation of your virtual partitions could slow things down quite a bit.

2) Have you manually profiled your boot sequence?  If so, make sure you haven't left the "profile" parameter in your kernel command line (If you don't know what I mean is you didn't do it).

3) Have you installed any new services?

In a more general sense it might be a good idea to check your logs for any errors or warnings.  You might also want to install bootchart to see what particular process or processes are holding up the boot process.

---

### Post by sammasaurus on 2010-02-10
I don't have my hdd partitioned, I have no idea what you're talking about, and no new additions.  I'm getting bootchart through synaptic; is there anything I need to do to turn on the recording/access the data?

---

### Post by RedSingularity on 2010-02-10
> **adam814 said:**
> I have a few questions that might narrow down potential problems for you:

1) Did you install using wubi?  If so it might benefit you to defragment your Windows drive as excessive fragmentation of your virtual partitions could slow things down quite a bit.

2) Have you manually profiled your boot sequence?  If so, make sure you haven't left the "profile" parameter in your kernel command line (If you don't know what I mean is you didn't do it).

3) Have you installed any new services?

In a more general sense it might be a good idea to check your logs for any errors or warnings.  You might also want to install bootchart to see what particular process or processes are holding up the boot process.


Thats what i thought at first too but he said that this slow down was very sudden and did not happen over time.  Thats what makes me think HDD pre-failure.

---

### Post by adam814 on 2010-02-10
You're right, as a hard drive begins to fail the failed reads will cause boots (or program loads for that matter) to take much longer than they should.  it wouldn't even be a bad idea to start backing up anything important just in case that is the problem.  It's just harder to troubleshoot hardware in a forum than software issues.

Maybe try the HD manufacturer diagnostic utility?  Some are (potentially) data destructive and some aren't.  Last year I did so with a Hitachi drive and after some googling I found out it would write to the last 8MB on the disk for the test, so I freed that much from the last partition before running it.  It turned out the drive was failing and the computer was less than 6 months old (got a new HD under warranty).

---

### Post by sammasaurus on 2010-02-10
Well, I keep my comp backed up, and I just got done updating it again, so I'm prepared (technically, but I think I might cry if I have to buy a new comp x.x).  Is there anything I can do at this point?  I'm definately not under warranty anymore, so I guess I'm just looking at prolonging my hdd's life until a later date.

---

### Post by flippo on 2010-02-10
If I were in your shoes I would check my HDD with something like the ultimate boot cd.  If your HDD is bad you can replace it and just restore your backed up machine.  Although, if your machine is 3.5 years it may be time to invest in a new one.

I personally have an rsync procedure set up to incrementally back up my machine to a server on my network, and when my computer goes down (my fault or not) I can just rsync it back to a working condition.

---

### Post by adam814 on 2010-02-10
> **sammasaurus said:**
> I don't have my hdd partitioned, I have no idea what you're talking about, and no new additions.  I'm getting bootchart through synaptic; is there anything I need to do to turn on the recording/access the data?

It stores the data as images in /var/log/bootchart.  You can just open them there.

---

### Post by john newbuntu on 2010-02-10
Check /var/log/dmesg for any problems/issues.  The column on the right gives the time after kernel boot.

---

