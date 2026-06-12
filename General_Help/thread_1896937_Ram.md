---
title: "Ram"
date: 2011-12-18
forum: General Help
---

### Post by nathan soulfly on 2011-12-18
hi i have ubuntu 11.10.my pc had 1G RAM and yesterday i ve installed one 1G RAM more so now i have 2G RAM.Will this effect the swap memory partition made when i installed ubuntu?partition was made for 1G RAM. HOW TO FIX IT?

THANX IN ADVANCE

---

### Post by 3rdalbum on 2011-12-18
With 2 GiB of RAM, it's perfectly possible to use no swap at all. I don't forsee any problems having a 1 GiB swap partition with 2 GiB of RAM.

If you really want, you can start up a Linux live CD and run GParted, and then resize the swap partition. But in your situation I wouldn't even bother to do that as there's probably no benefits.

---

### Post by The Cog on 2011-12-18
Your system should run as well or maybe better with the extra RAM and same size swap. 

The only issue you might have is with suspend, because I gather that the swap partition is used to store the RAM image. So for suspend to work, swap has to be slightly larger than the physical RAM. For that reason alone, you might want to do as 3rdalbum says and use a live CD to resize the partitions a bit. 

Do a backup first.

---

### Post by pretty_whistle on 2011-12-18
> **The Cog said:**
> Your system should run as well or maybe better with the extra RAM and same size swap. 

The only issue you might have is with suspend, because I gather that the swap partition is used to store the RAM image. So for suspend to work, swap has to be slightly larger than the physical RAM. For that reason alone, you might want to do as 3rdalbum says and use a live CD to resize the partitions a bit. 

Do a backup first.
In my case, the swap is 1.9GB but the ram is 2GB.  When I installed 11.04 it set this amount.  My suspend works ok though.  So...... what does mean?  Should I too enlarge the swap a bit?

---

### Post by pretty_whistle on 2011-12-18
Here's some FAQ about swap space if anyone needs it:


[https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

---

### Post by WorMzy on 2011-12-18
> **pretty_whistle said:**
> In my case, the swap is 1.9GB but the ram is 2GB.  When I installed 11.04 it set this amount.  My suspend works ok though.  So...... what does mean?  Should I too enlarge the swap a bit?

How frequently do you completely fill your RAM before using suspend?

---

### Post by pretty_whistle on 2011-12-18
> **WorMzy said:**
> How frequently do you completely fill your RAM before using suspend?
I don't know the answer to that.

---

### Post by pretty_whistle on 2011-12-18
I believe I have the answer to my question on the link I gave above.  The answer is that I don't need to add more.

---

### Post by georgemc on 2011-12-18
Threads discussing swap size are abundant on this forum and google, and opinions on swap size range from "do not need it" to a number of factors of ram size.

Swap will be used when a system runs out of RAM, I.e. many, many programs running, and when you "suspend to disk".  As long as you do not hit any of these conditions then your system will run just fine.

On a desktop with 2Gig plus RAM and low to moderate usage load, you most likely will not see the system swapping.  On a heavily loaded server this may be a different issue.

For todays desktop, laptops etc, it really depends on the users usage.  We do have tools to check this.

For example:
Open a terminal and type:
```

free -m

```It will produce an output similar to this:
```

              total       used       free     shared    buffers     cached
Mem:          3963       3136        826          0        335       1731
-/+ buffers/cache:       1070       2893
Swap:        10484          0      10484


```Look at the "-/+ buffers/cache: " line and in the "free" column you will see how much free memory you are currently have.  As long as that number is large and the "Swap: used" is zero or small then your system is not running out of RAM.

When I use my laptop I DO suspend to disk often and thus have the swap space sized to accommodate the "suspend to disk" operation which requires swap to be sized at least to the size of my RAM.

As a rule of thumb when I install a system I usually use a factor of 2 times the RAM size for my swap size.  I'm old school and this is what we used in our data centers.

Keep in mind that running a system into the swap carries a performance penalty with it.  RAM these days are clocked and run in nano seconds, and hard-drives, even the SSD's, run in mili seconds.  If my math is correct then that is a 1.000.000 time factor difference.  With this in mind you will notice a performance decrease when your system runs over the cliff into the swapping zone.

Happy swapping :KS

George

---

