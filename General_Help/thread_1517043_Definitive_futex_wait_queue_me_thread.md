---
title: "Definitive futex_wait_queue_me thread"
date: 2010-06-24
forum: General Help
---

### Post by Devil999 on 2010-06-24
#Note: Initially this was supposed to be a reply to a thread, but I thought maybe it was better if I started a new one, for centralization purposes.#

Everything was fine until my Amarok 2 stopped detecting my musics. When I closed it, instead of stop the process, it went into the futex_wait_queue_me channel. Then my Skype started having sound problems (after a few seconds in a call, I loose all the sound), and again, when I try to shut it down, it goes into futex_wait_queue_me.

The only way to deal with it is killing the process. But I can't find no way to prevent the problem. It's consistent and systematic. 

I've been searching around, and I've found several threads in this forum, and one of them had this [link]("http://fingergeek.blogspot.com/2009/05/cure-of-notorious-ubuntu-futexwait-bug.html"), explaining that it's a kernel problem, and saying that it was being solved. Thing is, that page is over 1 year old, as some of the threads in the forum that talk about this. I don't want to believe this is a problem that has been around that much time. 


Some of the threads that refer the same problem:
[1]("http://ubuntuforums.org/showthread.php?t=1395777")
[2]("http://ubuntuforums.org/showthread.php?t=1279035")
[3]("http://ubuntuforums.org/showthread.php?t=1243619")
[4]("http://ubuntuforums.org/showthread.php?t=1290763")


There are also some bugreports on launchpad with similar problems:
[1 - Main Bug]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/480497")

If anyone has anything to add, or maybe some solutions, please, do reply.

Note: I don't have Assistive Technologies enabled

---

### Post by Druegan on 2010-11-18
I don't know how much this problem has been around, but I keep my system monitor app open quite a lot, and I've only noticed this in the last week. In fact, I'm seeing a lot of strange stuff in there, and have no idea what any of it means..

The status of just about every process I'm using is "sleeping".. including Java, and I'm playing a java-based game that's currently running and is using 66% of my cpu.. how that's "sleeping" is beyond me..  It's also listed as "futex_wait_queue_me"..   So is Chrome, the browser I'm playing the game in.. sleeping and same waiting channel...

Of all the other processes running.. everything is in "poll_schedule_timeout", "futex_wait_queue_me", "do_wait", or "__skb_recv_datagram".  I've spent the last 40 minutes or so googling, but I can't even find out what these things *mean*.. if they're normal or not.. nothing.  Lots of questions asked on various forums.. very very few, if any, answers.  Nothing I can figure out, at any rate.


I'm running 10.04, and have assistive technologies disabled. The issues I started having came with a bunch of updates about a week ago.  The problems I get are:

Very long boot times.. system hangs excessively prior to bringing up the login..

Processes don't shut down when the application is closed.. specifically java and npviewer.bin seem to like to hang around when everything that should be using them has been closed.. which causes lots of problems when a new application using them starts..  double instances, resource conflicts, etc.. just chokes everything until all the processes are killed.

Certain applications also seem to hang in a non-functional state for 20-30 seconds when first initialized.  They appear to load, everything displays fine, but they allow no inputs.. clicking/typing is completely non-functional till it decides it's ready to allow it.  Again, Java/npviewer.bin seem to be the primary processes affected, but I'm pretty sure that's just because it's what I use the most.

I'm running the latest Sun JRE, and that hasn't been updated.. there was just something in the batch of updates a week-ish ago that doesn't play nice with the rest of the OS. 

But yes, any input or answers would be delightful.

---

### Post by abab32 on 2011-01-21
Hi,

what I can tell from my experience with programing under linux is:

Such a thing happens when one wants to implement a multi threaded program using a shared queue. The different threads want to get some data from the queue and sometimes it happens that one thread is occupying the queue and the other threads are waiting for the queue to be freed. At this moment it can be seen that only one thread is working and all other threads are waiting for the queue. This scenario often happens when programming with python due to the existing threading issues with the python GIL. It can also be seen that only one CPU is used, although several threads are running. Thats what I can say..

---

### Post by smokes2345 on 2011-01-27
I can also confirm this issue although I have only seen it when trying to run WoW.exe, everything else seems to be working fine.

---

### Post by .jekyll on 2011-02-24
I was having the same problem. I'm running Amarok 2.3.0 on Lucid Lynx  and the exit command didn't work - either by using the "Amarok ->  Quit" menu item, or right clicking on the tray icon and choosing "Quit".  I had to use the system monitor to end the process, that got stuck in that "futex_wait_queue_me".

So far, the solution suggested on this thread seems to have fixed it (yay! :) ):
[http://ubuntuforums.org/showthread.php?t=1581623](http://ubuntuforums.org/showthread.php?t=1581623)


This is the relevant post:
> **mc4man said:**
> You could try this - (you may need to remove amarok then re-install it, maybe not
```
sudo apt-get install mysql-server-core-5.1
```old, related bug  concerning music collection, an unclean shutdown was also seen.
[https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269](https://bugs.launchpad.net/ubuntu/+source/amarok/+bug/523269)
[http://ubuntuforums.org/showthread.php?t=1518936](http://ubuntuforums.org/showthread.php?t=1518936)

don't know much about the wallet deal, I just click thru it once and it thankfully never shows up again

Have you tried this?

---

### Post by spedoinkle on 2011-06-14
> **abab32 said:**
> 
Such a thing happens when one wants to implement a multi threaded program using a shared queue...It can also be seen that only one CPU is used, although several threads are running. Thats what I can say..

echo 1 > /sys/devices/system/cpu/sched_mc_power_savings

meh?

---

### Post by spedoinkle on 2011-06-14
1710 /**
1711  * futex_wait_queue_me() - queue_me() and wait for wakeup, timeout, or signal
1712  * @hb:         the futex hash bucket, must be locked by the caller
1713  * @q:          the futex_q to queue up on
1714  * @timeout:    the prepared hrtimer_sleeper, or null for no timeout
1715  */
1716 static void futex_wait_queue_me(struct futex_hash_bucket *hb, struct futex_q *q,
1717                                 struct hrtimer_sleeper *timeout)
1718 {
1719         /*
1720          * The task state is guaranteed to be set before another task can
1721          * wake it. set_current_state() is implemented using set_mb() and
1722          * queue_me() calls spin_unlock() upon completion, both serializing
1723          * access to the hash list and forcing another memory barrier.
1724          */
1725         set_current_state(TASK_INTERRUPTIBLE);
1726         queue_me(q, hb);


here is your futex_wait_queue_me from the kernel.

---

### Post by deejaylight on 2012-06-08
Same problem with ubuntu 12.04 and skype

---

