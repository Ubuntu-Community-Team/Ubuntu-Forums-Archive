---
title: "So many problems, where do I begin?"
date: 2009-08-02
forum: General Help
---

### Post by jdeppel on 2009-08-02
I'm fairly new to Ubuntu (about a year and a half now), so bear with me, but I'm about ready to throw my system out the window due to the immense amount of trouble it has been causing me as of late.

I've been running 9.04 since release date. Everything worked flawlessly until about a week or so ago. Let me list the problems I started noticing around then:
X-server randomly crashing and returning me to the GDM login window
Applications closing at random
Random lockups
Frequent kernel panics during startup (in verbose mode: "Kernel panic - not syncing: Attempted to kill init!)
When I don't receive a kernel panic, the ubuntu loading window will lockup at random points
If I DO get to my desktop, I can't start synaptic or Update Manager (I'll see "Starting Administrative Tasks" in the panel, which then disappears after a long pause, without the app starting. My desktop will then lockup, though I can still move the mouse, just can't interact with anything on the desktop).

I've reinstalled 9.04 probably about 5 times in the last week, and always seem to end up with the same problem. I'm seriously considering downgrading back to Intrepid or Hardy and see if that would alleviate my problems, but for some reason I'm slightly hesitant to do so. 

Running fsck and memtest show no obvious issues. (Though fsck did one time find a problem, which it fixed, with the root partition, but the problems remained)

With so many issues, I'm not even sure where to start, as I'm not sure if the errors I have are mearly cascading on one another. 

Any ideas?   :confused:

---

### Post by credobyte on 2009-08-02
Try downgrading your kernel ( btw, what's your current kernel version ? ).

---

### Post by DeMus on 2009-08-02
Are you sure you have enough disk space on all drives?

---

### Post by jdeppel on 2009-08-02
@credobyte
The kernels I currently have available to me are:
2.6.28-14
2.6.28-11
However, I receive the problems on either kernel

@DeMus
Yes. I currently have one HD with one partition on it. The HD is 250GB.

---

### Post by jdeppel on 2009-08-02
Okay...check this:

I just had Firefox close on me while I'm running my 8.04 Live CD. 

WTF is going on?

---

### Post by credobyte on 2009-08-02
Do you see anything "weird" in your system log files ( dmesg and syslog ) ?

---

### Post by DeMus on 2009-08-02
> **jdeppel said:**
> Okay...check this:

I just had Firefox close on me while I'm running my 8.04 Live CD. 

WTF is going on?

When you have the same problems on a live cd as well, it is not your installation, it must be hardware related.
Just boot with the cd and use memory test. Let it run for a long time to see if anything goes wrong here.

---

### Post by merlinus on 2009-08-02
Sounds like hdd or memory problems, especially since you are getting crashes whilst running from the live cd, which is in RAM.

You can do a memtest from the grub menu.

---

### Post by jdeppel on 2009-08-02
> **DeMus said:**
> When you have the same problems on a live cd as well, it is not your installation, it must be hardware related.
Just boot with the cd and use memory test. Let it run for a long time to see if anything goes wrong here.

I'll let the memtest run for several hours and post the results after I get some sleep.

> **credobyte said:**
> Do you see anything "weird" in your system log files ( dmesg and syslog ) ?

Since I'm still pretty new to Ubuntu, I still have no idea how to read log files, though I've never tried. When I post after some sleep, I'll post the output of those two files.

---

### Post by credobyte on 2009-08-02
> **jdeppel said:**
> I'll let the memtest run for several hours and post the results after I get some sleep.



Since I'm still pretty new to Ubuntu, I still have no idea how to read log files, though I've never tried. When I post after some sleep, I'll post the output of those two files.

```
System -> Administration -> Log file viewer
```
** smth like that .. I'm running localized version of Ubuntu :)

---

### Post by jdeppel on 2009-08-02
Okay. It looks like one of my RAM sticks is hosed. 8 hours, 26 errors. It all looks like it's just one module though (judging by the addresses). I have no idea how the other memtests passed. Maybe an intermittent error. 

Looks like I'll be dropping down to 2GB of RAM instead of 3. :frown:

---

### Post by jdeppel on 2009-08-10
I removed the bad RAM stick. Ran a memtest, let it run for 10 hours, and received 0 errors.
 

 However, I'm still having problems.
 

 I managed to get Hardy to install. For some reason, I can't get Intrepid or Jaunty to install. Whether I use the LiveCD or my current Hardy installation, I still receive random applications closing, applications not starting, and random Xserver crashes.  
 

 If I attempt to boot up the LiveCD of Intrepid or Jaunty I typically receive one of two errors on bootup:
 Error: Bad EIP value
 Kernel panic – not syncing: Attempting to kill init!
 Other times, it will sometimes just lockup at a random point.
 

 My question is, if my RAM is now (presumably) good, why am I still experiencing problems, especially with the LiveCD? I've tried the remaining two RAM sticks individually in all three slots, and receive the same error each and every time.  
 

 Does anybody have any pointers or thoughts?

---

