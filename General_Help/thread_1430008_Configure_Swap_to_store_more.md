---
title: "Configure Swap to store more?"
date: 2010-03-14
forum: General Help
---

### Post by TheGreatBunghole on 2010-03-14
I was just wondering if there was a way to configure Swap to store more, even when the RAM isn't near-full?

I think this would be a good thing for people with SSDs, to free up more RAM. Maybe on a netbook with small amount of RAM?

This is just a thought. I am not really expecting a quick answer.

I only have 1 GB RAM on my laptop that is 3 years old, and of that 1 GB, the graphics card takes up 256 MB RAM. I currently have it set to use only 128 MB RAM, so I am running Ubuntu 9.10 with only 896 MB RAM (although in the system monitor it shows up at 874.6 MB. I could be using 600 MB of my RAM, and Swap will be at 0%.

If I were to get an SSD, and find a way to configure Swap to be utilized more of the time when, say the computer is idle. Then the RAM would be cleared up a bit more for say, Cache? Then hypothetically, I would be able to immediately start clicking away on everything!  ...right?

I am not worried about the CPU though, because it is an AMD Turion 64x2 1.8 GHz. It runs flawlessly. If anyone has any ideas on how swap can be utilized more often than not, please reply.

:D
,Alex.

---

### Post by asmoore82 on 2010-03-14
Any hard drive, SSD or not, will still be orders of magnitude slower than the RAM.

And programs still never actually get to run out of Swap space. They must be
off-loaded to and re-loaded off of the hard drive as a last resort when
the RAM is full, hence the term "swap."

It's good that you are thinking about such things though :D.
If you really want to affect the kernel's Swap strategy, you can modify
the "vm.swappiness" value with the utility `sysctl` ...
```
#check it
sysctl vm.swappiness
#tweak it
sudo sysctl vm.swappiness=20
```
^higher values make the kernel more willing to resort to Swap

To make the change permanent, you would have to add it to the file "/etc/sysctl.conf"

If you are curious about my RAM vs. SSD generalization,
DDR400 RAM, for example, has an effective clock of 400 MHz and a 64-bit wide bus
Multiply that out for a theoretical maximum throughput of 25.6 Gigabits per second.
But the fastest SATA interface on any SSD will max out at 3 Gigabits per second.

---

### Post by TheGreatBunghole on 2010-03-14
So since we have the technological know-how to create RAM that is that fast, then why aren't storage devices &/or interfaces faster?  Would it have anything to do with a slow connection to storage devices on the mobo? But then again I better not keep asking questions, because eventually somebody will ask me to post it in some other forum. :)

I do know that processes can't really run from swap. But thank you for giving me the information on how to change the "swappiness" values. It is actually exactly what I was hoping for! :D

But another question (sorry) -  Should there be an option in an install of Ubuntu for people with SSDs to have the "swappiness" set a bit higher than normal, for better performance?

---

### Post by asmoore82 on 2010-03-15
> **TheGreatBunghole said:**
> But another question (sorry) -  Should there be an option in an install of Ubuntu for people with SSDs to have the "swappiness" set a bit higher than normal, for better performance?

Someone correct me if I'm wrong, but higher swappiness can never
increase performance of interactive userspace applications.

Swap in this context is always a last resort for a system that could benefit from more RAM.

---

### Post by QIII on 2010-03-15
Why aren't storage devices faster?  

There are physical limitations to disk technology.  Actual bits and pieces have to move mechanically.  But they can be improved.  Things like SATA rev 3 specifications are indications that they will become faster.

What about SSDs?  Theoretically, they could run faster.  They eventually will.  Technology evolves.  But a big problem with current SSD technology is the relatively short "wear out" on the read/write cycle.

Your machine "runs" in memory.  It "refers" to storage.  Memory is already getting faster.

---

