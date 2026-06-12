---
title: "Fsck uses a ridiculous amount of memory and aborts with memory allocation failed"
date: 2010-11-25
forum: General Help
---

### Post by reffu on 2010-11-25
I was shrinking a partition the other day and there was a brown out and now I can't get into my partition even with testdisk. When I run fsck it gets to a point where it pauses for a while and then stops and gives me 

```
Illegal block #269485068 (3712109856) in inode 2087157.  CLEARED.
Error storing directory block information (inode=2087157, block=0, num=190005956): Memory allocation failed
e2fsck: aborted
```

When I look at my memory usage in the system monitor it jumps from 200 mb to 600 mb to 1.3gb to 1.8gb to 2.7 gb where it stops (I'm running on a 32 bit live cd with 4 gb of ram of which 3gb isd available) 

Regardless of what's wrong with the drive I have tried multiple solutions to get fsck to finish.

I have increased my swap to 6gb and turned my swappiness up to 100 but fsck eats up memory so fast it doesn't get a chance to transfer more than about 20mb to swap

I have edited /etc/e2fsck.conf to add scratch files but the same as with swap the cache files are only about 10mb when it runs into the memory allocation error. 

The speed at which my memory disappeared makes me think that even using a 64 bit live cd with my full 4gb wouldn't help.

Does anyone have any suggestions on how to stop it from using so much memory or force it to run in swap?

Thanks,

Reffu

---

### Post by ajgreeny on 2010-11-25
To force an fsck on an OS partition at boot time you can use the command ```
sudo touch /forcefsck
```

I wonder if it is possible to make that same command carry out the fsck on any other partition with ```
sudo touch /forcefsck /dev/sdx#
```  I have no idea whether or not that even works, or if it does, whether it would help overcome your problem, but just throw out the idea as something to investigate further.

---

### Post by reffu on 2010-11-25
Thanks but my problem isn't having it run at boot its stopping it from eating my memory.

---

### Post by ajgreeny on 2010-11-25
Yes, I accept that, but if you get it to run at that point on the faulty partition, it may clean up problems without causing this huge memory usage.

I'm just thinking aloud really, and the "touch file" way may not even be possible.

---

### Post by reffu on 2010-11-28
Unfortunately the only way I can run fsck is from a live usb stick without any persistence so running touch would be lost on reboot.

---

