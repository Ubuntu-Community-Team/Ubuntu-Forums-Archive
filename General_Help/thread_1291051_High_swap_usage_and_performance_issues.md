---
title: "High swap usage and performance issues"
date: 2009-10-14
forum: General Help
---

### Post by empty_spaces on 2009-10-14
I use 64bit Jaunty and I have noticed lately that my swap usage goes up steadily when I am copying files to and from my external USB drive.(currently, my swap is showing 3.4GB used out of 3.8GB) which leads to some performance issues.
I have 4Gb of ram. 

I am thinking of disabling swap to see what would happen. Is that safe to do? And is it easily reversible? 

And what's the best way to disable swap?
I've read about a couple of ways 1) edit fstab 2) via Gparted. 
Any other better options?

Thanks.

---

### Post by justleen on 2009-10-14
```
 sudo swapoff
sudo swapon -a
```

And yes, its quite safe to turn off swap.
Keep an eye on your memory.. normally when there is no free mem, your systems starts swapping

---

### Post by empty_spaces on 2009-10-14
Thanks for the reply.
Can I run that command even when swap is 80% full, or would it be better if I restarted the system before I run the command?
My ram usage is usually around 1GB with all the normal programs running. It goes up to about 2.5GB when I have a couple of VMs running, but it almost never goes beyond 3GB.

---

### Post by justleen on 2009-10-14
Not sure what happens turning it off when its used..

Just did a small test: copied several ISO's to a 2GB stick,and I see the same happening.. when free mem is running low, it starts swapping, load goes up..
Open a terminal, run "watch free" and then repeat your copy action.. you should see the same with men/swap happening.

Once its done copying, it starts freeing the stuff up again, load drops quite quickly.
Seems that a copy action simply buffers to RAM, and offcourse when it runs out of ram, it starts swapping..

Edit: Yes, its safe to run "sudo swapoff -a" when its in use ;)

---

### Post by empty_spaces on 2009-10-14
Just did the same experiment, and you are right. It does look like I am maxing out my ram during file copies and it then switches over to swap.

Attached a couple of screenshots of System monitor and "watch free". My used ram is still pretty much maxed out after the file transfers if I go by the "watch free" numbers.

The "watch free" command shows a much higher ram usage than the one shown in System Monitor. Why is that? The swap usage shown by both is roughly the same but not the ram usage.

---

### Post by oldos2er on 2009-10-14
Have you played with the swappiness setting? [https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27](https://help.ubuntu.com/community/SwapFaq#Performance%20tuning%20with%20%27%27swappiness%27%27)

---

### Post by empty_spaces on 2009-10-14
I had forgotten about the swappiness setting. Thanks for reminding me, oldos2er.
I went ahead and set it to 10, restarted the system and did a couple of file transfers to my external drive and started a couple of VMs. No swap usage so far and everything seems to be a lot snappier.
So it's looking good so far. I'll monitor it for a couple of days.

---

### Post by XCan on 2009-10-14
> **empty_spaces said:**
> 
The "watch free" command shows a much higher ram usage than the one shown in System Monitor. Why is that? The swap usage shown by both is roughly the same but not the ram usage.

They seem to be consistent, you have to compare with the second line of "free". The buffer is just there to help use as much of your RAM as possible and will be cleared when needed, but it doesn't really constitute what your system is requiring at the time of query.

---

### Post by empty_spaces on 2009-10-14
> **XCan said:**
> They seem to be consistent, you have to compare with the second line of "free". The buffer is just there to help use as much of your RAM as possible and will be cleared when needed, but it doesn't really constitute what your system is requiring at the time of query.

Oh ok. I guess I was reading it wrong.

It is now about 5 hours since I set my swappiness to 10, and I have never seen Ubuntu run this fast. Before the change, I would always hear my HDD grinding everytime I did some stuff, but now everything just moves along very smoothly.
Also, it looks like my laptop is running much cooler due to reduced HDD reads/writes.

---

