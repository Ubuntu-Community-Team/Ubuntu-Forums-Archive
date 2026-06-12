---
title: "800mb of ram used when i log in ?"
date: 2009-07-19
forum: General Help
---

### Post by Shpongle on 2009-07-19
iv 2gigs of ram , when i log in 800mb is being used up?, and i cant see whats using it, i have compiz and cairo dock running at start up also iv 5gb of swap and that is never used, also i set vm.swappiness = 10 ,  

i cant find whats eating up the memory any idea? i ran top just after logging in , iv added a screenshot

---

### Post by blueridgedog on 2009-07-19
Are you unhappy that the ram is being used or unhappy that the system isn't using more?  Empty memory is wasted memory and the system on boot will hold a lot of files in memory until it has a reason to free the space.  What is the output of:

```
free
```

---

### Post by Shpongle on 2009-07-19
thanks for getting bk to me , no its just that it seems a like a lot of memory to have used before i start anything, im aware that background processes ect are running, it just seems like a lot of memory for that, im using preload and prelink , i assumed it was loading the files into memory to load faster on startup, here is the output of free  

```

dill@ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       2052328    1998872      53456          0      38672    1558148
-/+ buffers/cache:     402052    1650276
Swap:      5316472          0    5316472
dill@ubuntu:~$ 

```

---

### Post by mgranet on 2009-07-19
You are only looking at ~400MB active useage. Looks pretty good to me. You can also add the -m switch to the free command to display free's output in a more human-readable format.

---

### Post by Shpongle on 2009-07-19
ok thanks, yea 400 looks normal for what im doin , so does top include the cached memory in the used output?

---

### Post by mgranet on 2009-07-19
Yeah. It just reports all memory used by anything, including buffers and cache. A full cache is a very good thing, as it improves system performance.

---

### Post by Shpongle on 2009-07-19
ok thanks, is there much point in me having a swap partition sees as tho its never used? , iv been reading up on tuning the swappiness, i have mine set to 10 (from what iv read its supposed to make the system more responsive and reduces dependencies on swap ),

---

### Post by mgranet on 2009-07-19
There is debate on this. I tend to use swap, since I use a virtual machine, even the 2GB I have is not sufficient in that case.

---

### Post by Marlonsm on 2009-07-19
Linux knows that unused RAM is wasted RAM, so if it notes that there is too much RAM few a few programs, it starts loading stuff you might need on the RAM, so the computer will get faster. As soon as it notes you need that RAM back, it will unload all exceeding stuff.


> **mgranet said:**
> There is debate on this. I tend to use swap, since I use a virtual machine, even the 2GB I have is not sufficient in that case.

Even then, you don't really need swap.
The only time I remember seeing my swap used, I was with two virtual machines (one XP and one Android), some apps open (Google Earth, RecordMyDesktop, Firefox, Kdenlive...) and encoding a video in the background, all of that with Compiz and Emerald running. With 2Gb of RAM. And it just used some 50mb of swap. And I still had some 500Mb of free RAM.

---

### Post by Shpongle on 2009-07-19
so should i resize my swap or change the swappiness or just leave as is?, the main reason i started this thread was my system lags at times , and i thought it was memory related ,

---

### Post by 3rdalbum on 2009-07-19
If you're not using any of your swap, then it's not impacting on performance. Linux generally doesn't try and use swap until your real memory is filling up a bit.

If you wanted to completely prevent Linux from using swap, you can use this command:

```
sudo swapoff -a
```

Note to others: **Be careful in using this command.** If you don't have enough RAM to do what you want to do, then the system will start thrashing and the only way to stop it is to press the reset switch on the front of your computer.

---

### Post by Shpongle on 2009-07-19
ok thanks i think il just keep the swap enabled just in case , and il resize it , thanks for all the help and suggestions

---

### Post by blueridgedog on 2009-07-19
> **DillByrne said:**
> so should i resize my swap or change the swappiness or just leave as is?, the main reason i started this thread was my system lags at times , and i thought it was memory related ,

I think the default is fine.  You have memory to spare and your system is caching what it can.  Any swapping is bad, but better than not having swap when you need it.  It is simply a very inefficient way to emulate system memory, but it is the only game in town once your run out of the real stuff (unless you want to get into Vista's "ready boost" and the use of a flash drive as a type of swap).

I say compute on and don't look back.  When your system get sluggish, run free again and see what is going on.

---

### Post by Shpongle on 2009-07-19
ok thanks i will do,  il be staying as far away from vista as possible:D

---

### Post by mgranet on 2009-07-19
> **Marlonsm said:**
> Linux knows that unused RAM is wasted RAM, so if it notes that there is too much RAM few a few programs, it starts loading stuff you might need on the RAM, so the computer will get faster. As soon as it notes you need that RAM back, it will unload all exceeding stuff.




Even then, you don't really need swap.
The only time I remember seeing my swap used, I was with two virtual machines (one XP and one Android), some apps open (Google Earth, RecordMyDesktop, Firefox, Kdenlive...) and encoding a video in the background, all of that with Compiz and Emerald running. With 2Gb of RAM. And it just used some 50mb of swap. And I still had some 500Mb of free RAM.

I'm running an x64 system, which consumes a bit more ram. I also like to assign a large portion of RAM to my VM's (cache is good even in a VM), which in my case, leaves me running several hundred megs into swap. Could I eliminate swap? Sure. But my host machine's performance would suffer. Hence, the great swap debate. Hopefully, in the near future this will become a thing of the past, as RAM prices are getting cheap and capacities are soaring, even power users should be able to have enough RAM on hand to eliminate swap entirely.

---

