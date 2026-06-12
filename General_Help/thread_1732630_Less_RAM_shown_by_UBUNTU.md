---
title: "Less RAM shown by UBUNTU"
date: 2011-04-18
forum: General Help
---

### Post by Ronalddig on 2011-04-18
hi
i am new user to ubuntu .

my main problem is :

1. I have 4 GB of DDR3 RAM but ubuntu shows only 3GB available.

the result of free are :


>             total       used       free     shared    buffers     cached
Mem:       3086992     985428    2101564          0      61212     488768
-/+ buffers/cache:     435448    2651544
Swap:      7812092          0    7812092


why is this ??

Thx in advance :)

---

### Post by blah... on 2011-04-18
Did you install the 32-bit version if Ubuntu? You will need the 64-bit version in order to fully utilize all 4 GB of RAM.

---

### Post by Ronalddig on 2011-04-18
hi
thx for your answer

yes , i did install 32 bit ubuntu . this is because when i was reading forum i found few people having trouble with 64 bit.

Moreover i think 32 bit supports upto many GB of RAM .

why is it restricting itself to only 3 GB ??

---

### Post by Sef on 2011-04-18
> yes , i did install 32 bit ubuntu . this is because when i was reading forum i found few people having trouble with 64 bit.

Moreover i think 32 bit supports upto many GB of RAM .

why is it restricting itself to only 3 GB ??

The 32-bit version can only read 3.2 GB. To get it to read more, you have to install PAE.

---

### Post by mcduck on 2011-04-18
32-bit operating systems are only able to address up to 4GB of memory, which includes memory addresses used for other purposes than just the RAM, like the memory in your graphics card. As a result, you only get around 3GB of addressable RAM with a normal 32-bit OS, depending on how much graphics memory you have.

Ubuntu does have a PAE-kernel which allows the 32-bit OS to use more RAM. You can install that with Synaptic Package Manager if you want to, although it will decrease performance a bit compared to normal kernels.

In general I'd recommend installing the 64-bit version of Ubuntu instead, it should work just fine for most people, and only go for the 32-bit PAE kernel if you know that you can't use the 64-bit one (for example because there isn't a 64-bit compatible version of some program or driver you are using).

---

### Post by Ronalddig on 2011-04-18
thx sef and mcduck for your solution.

i just installed pae and i see 4 GB of ram :)

I would also update to 64 bit ubuntu on next release by fresh installation.

also , while i was reading abt pae , one person recommended it saying that 64 bit wastes much memory compared to 32 bit , so pae is better , whereas mcduck says that pae would leads to a bit of degradation in performance.

---

### Post by mcduck on 2011-04-18
> **Ronalddig said:**
> thx sef and mcduck for your solution.

i just installed pae and i see 4 GB of ram :)

I would also update to 64 bit ubuntu on next release by fresh installation.

also , while i was reading abt pae , one person recommended it saying that 64 bit wastes much memory compared to 32 bit , so pae is better , whereas mcduck says that pae would leads to a bit of degradation in performance.
32-bit and 64-bit both have their good sides and bad sides. 64-bit system will use slightly more RAM, but it's ability to address more RAM will easily compensate for that and you'll end with more free RAM anyway. And depending on what you use your computer for it might give you a decent boost in processing power as well.

PAE kernel on the other hand needs to do some extra work to translate memory addresses, thus giving you the ability to use more RAM but at the cost of loosing some CPU time (and not having the boost 64-bit processing gives to certain tasks).

So in the end if you have much RAM on your system then a 64-bit kernel will indeed give you the best result, while a PAE kernel is only a decent workaround in case you cant run a proper 64-bit OS for some reason or other.

And the plain old 32-bit (normal) kernel has slightly smaller memory usage but of course lacks the ability to address large amounts of RAM and all the performance benefits of a 64-bit system. It might be a good choice even on a 64-bit capable system if you have less than 4GB of RAM ad don't do any tasks that benefit from 64-bit computing.

---

### Post by Ronalddig on 2011-04-19
thx for detail info :) really appreciated .

also lastly , since i am new to ubuntu , I want to read some book regarding this 

i have basic knowledge of UNIX and linux commands.

since there are so many books, its difficult for me to decide .

Can anyone recommend some good books which gives me basics of ubuntu linux .

thx

---

### Post by 3rdalbum on 2011-04-19
If you've got DDR3 RAM, then your CPU most likely supports 64-bit; so why not just use the 64-bit edition? If you don't want to reinstall Ubuntu right now, then either live with 3.2 GiB of RAM or install the PAE kernel until you're ready to do your next reinstall.

64-bit uses slightly more RAM because the memory addresses are longer, but at least your CPU doesn't have to convert memory addresses from 32-bits to 36-bits every time a program wants to get at some RAM.

---

### Post by Ronalddig on 2011-04-19
thx 3rdalbum for help
i have installed PAE , would upgrade to 64 bit on next release

---

### Post by harsh2209 on 2012-01-11
Hi All,

I have the similar issue. I have installed 64bit Ubutnu 11.10, yet the System Information shows only 7.7 Gb instead of full 8GB. I've attached a screenshot.

The BIOS reads full 8 GB. Any suggesitons..?

Thanks

---

### Post by CharlesA on 2012-01-11
On board video memory.

```
free -m
```

Will also tell you how much memory you have available.

---

### Post by harsh2209 on 2012-01-11
> **CharlesA said:**
> On board video memory.

```
free -m
```

Will also tell you how much memory you have available.
Thanks very much Sir! I read a 'Solved' thread about this as well. Appreciate your information and direction.

---

