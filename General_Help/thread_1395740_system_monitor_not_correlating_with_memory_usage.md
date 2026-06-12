---
title: "system monitor not correlating with memory usage?"
date: 2010-02-01
forum: General Help
---

### Post by princeofnam on 2010-02-01
in this example, my memory 993.4 MiB memory is said to have 575.9 MiB of it used and 163.4MiB of my 2.8 GiB swap memory used. but in my processes tab, the most memory hogging program is 98.3 MiB, and Pidgin, 25.9 MiB, and 18.9 MiB, 14.9, 6.2,6.1,5.2,3.4,3.3,1.8,1.8,1.7, etc.  I'm certain these don't add up to 575.9 MiB so where is all this extra memory usage coming from?

also, why is data measured in MiB?

---

### Post by mcduck on 2010-02-01
Data in computer memory is measured in Ki, Mi etc format since that's how all computer hardware works, they are based on binary mathematics, calculating with bits. 8 bits gives you ability to count up to 2^8 = 256, 9 bits would gve you 2^9 = 512, 32 bits gives you 4294967296 and so on. So the way outr cmputers work doesn't result in even numbers on a decimal system, only on binary system.

Calculating data in memory, or actually in most computer-related purposes, is based on binary measures simply because that's how the computers handle data.

For hard drives using normal decimal-based multpliers, (k = 1000 instead of Ki=1024) is accepted since in theory hard drives could store raw data as bits instead of using set amonts of data like computers do (computers usually handle stuff like bytes (8 bits) and words (usually 32 bits)). Same applies to networking, network speeds are also mesured in bits asince a network device could also in theory transmit single bits instead of full bytes.

(I must add that I really dislike the hard drive manufacturer's way of measuring data in decimal multipliers since in reality it will still be used as binary measures. Even though it's thoretically possible, I've never heard of any system storing single bits to hard drives...)

Anyway, what comes to your memory usage there are several things to keep in mind. Even the programs that use too little memory to really show in system monitor apps, they still use some, and addign together all memory usage from all small processes will definitley result in higher than zero value. And second, different applications show different values for memory usage because they count the amount of free RAM in different ways. For example some might consider RAM used as cache as used memory (since it is in *some* use), while others count it as free memory (since it's still free for any program to sue, should they need it).

To check how much RAM your system and programs are using, run "free -m" and read from the "-/+ buffers/cache"-line. :)

edit: here's an example:
```
mcduck@Hyperion:~/Desktop$ free -m
             total       used       free     shared    buffers     cached
Mem:          2013        412       1601          0         49        149
-/+ buffers/cache:        212       1800
Swap:         1498          0       1498
mcduck@Hyperion:~/Desktop$
```
My laptop has 2013Mib of available RAM (2GiB minus the amount of memory Linux kernel takes in RAM, ythat doesn't count as available since it's not possible to use that part of memory for anything else, you need to have the kernel there for the system to work)

From that 2013Mib a total of 412Mib is in *some* use. 212Mib is used by applications, 49Mib is buffers and 149Mib is used to cache some recently accessed data. (I just booted the laptop so there isn't much cached data yet.)

1601Mib is completey unused, while programs actually have 1800Mib of RAM they can use any time they need to (cached data can be dropped if more RAM is needed).

..and there's also 1498Mib of swap space, which is completely unused. After running a while there will suually be a couple of megabytes of cache use even if there's plenty of RAM, bacause Linux kernel uses a bit of swapping as a way to check what things should be still kept in cache and what can be dropped). Also the cache will grow to fill all the RAM that isn't used for anything else.

---

### Post by princeofnam on 2010-02-01
my problem is.  when i add the memory values together, all the ones in the MiB range add up to ~207 MiB right now under processes.  but under resources, i'm said to have "789" in some use, as you phrased, and "577" in use my applications.  now, i don't think the other processes amount to anymore than 60, and they're all in the KiB range, so i can conceive of no way they'd make up that difference between 207 and 577.  am i still misunderstanding something?

---

### Post by princeofnam on 2010-02-02
sorry. i want to bump this topic again.  i  seriously want to get to the bottom of memory usage issue.

---

### Post by floborg on 2010-03-13
Could it be that System Monitor is showing virtual memory use on the graph?  I just upgraded from Jaunty to Karmic and noticed my memory use jump from about 160-190 MB on startup to ~650 MB.  Like you, there's nothing on the processes tab hogging memory.

---

### Post by SilverWave on 2011-06-18
> **princeofnam said:**
> sorry. i want to bump this topic again.  i  seriously want to get to the bottom of memory usage issue.

Yeah yeah old thread :-)

But I was researching this issue and came up with this thread :-)

```
$ free -m
             total       used       free    buffers     cached
Mem:          8000       7686        314       2300        774
-/+ buffers/cache:       4612       3388
Swap:         8191          0       8191
$ 
```4.5Gib in Resources tab.

hmm... 
2300+744=3074

3074-4612=1538

1471 is the total displayed in Processes down to <1MiB

Good enough for me ;-)

Buffers & Cached accounts for the difference.

---

### Post by KTrigger on 2011-07-21
Actually you are missing 3GB of RAM somewhere. The 4612 figure already has the buffers and cache accounted for.

7686-3074=4612

---

