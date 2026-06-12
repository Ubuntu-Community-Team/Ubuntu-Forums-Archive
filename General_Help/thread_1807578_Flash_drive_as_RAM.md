---
title: "Flash drive as RAM??"
date: 2011-07-19
forum: General Help
---

### Post by khaj_vah on 2011-07-19
Hello everyone 


People i think it is possible to use Flash drive as ram because flash drive can do what RAM does.it is just interesting so if someone has an idea pls let me know :)

---

### Post by haqking on 2011-07-19
> **khaj_vah said:**
> Hello everyone 


People i think it is possible to use Flash drive as ram because flash drive can do what RAM does.it is just interesting so if someone has an idea pls let me know :)


RAM is much faster than any card reader or USB device, i suspect you are referring to the Readyboost technology in windows which is not supported in Linux.

BUY more ram it is cheap enough, or create a the correct swap partiton.

you could in theory create a swap partition on your flash drive.

i dont think there is any such technology in Linux though someone might correct me.

readyboost dont do much anyways, it is pretty poor, RAM is so much faster than external access methods

---

### Post by khaj_vah on 2011-07-19
well the problem is that my computer is old and has DDR1 and i cant find DDR1 ram to upgrade:) but anyway it is interesting if it is possible or not

---

### Post by khaj_vah on 2011-07-19
i havent heard of readyboost i just thought that it can do the function that RAM  is doing

---

### Post by haqking on 2011-07-19
> **khaj_vah said:**
> i havent heard of readyboost i just thought that it can do the function that RAM  is doing


memory management is superior in linux than windows anyways IMO.

as for using external devices as RAM, it is not the same (which is why readyboost is not really popular)

buy more ram if you can find it, setup appropriate swap or upgrade computer.

even if you could use a 8GB flash, it wouldnt give you 8gb extra ram which is what i think you are after.

it just doesnt work like that

---

### Post by khaj_vah on 2011-07-19
ok mate thanks for help

---

### Post by Mark Phelps on 2011-07-19
ReadyBoost is not what you want, anyway.  It's a caching feature that allows the CPU to pipeline more instructions, and it only helps in situations where the PC has very little memory to start with.  It does NOT add to the supply of System Memory.

---

### Post by TheNosh on 2011-07-19
> **haqking said:**
> memory management is superior in linux than windows anyways IMO.


What do you base this off of?

---

### Post by haqking on 2011-07-19
> **TheNosh said:**
> What do you base this off of?

Windows utilises pagefiles instead of dedicated swap partition areas allowing Linux users to modify how long a process stays in RAM as oppose to swapped out, windows does not allow for this. Though pagefiles can be placed elsewhere such as a seperate disc but this is not default and windows cant create a memory dump.

On top of this linux and its filestystems is less prone to fragmentation where as under windows this can lead to slower performance times when it comes to virtual memory.

---

### Post by TheNosh on 2011-07-19
> **haqking said:**
> Windows utilises pagefiles instead of dedicated swap partition areas allowing Linux users to modify how long a process stays in RAM as oppose to swapped out, windows does not allow for this. Though pagefiles can be placed elsewhere such as a seperate disc but this is not default and windows cant create a memory dump.

On top of this linux and its filestystems is less prone to fragmentation where as under windows this can lead to slower performance times when it comes to virtual memory.

[http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux#Performance](http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux#Performance)

Read this. Basically, swap partition are of little use on desktops. And Windows has had intelligent block allocation on NTFS since XP.

Also, a simple de-fragmentation, if done semi-regularly, should take very little time.

I ran Linux with no swap partition or swap file for a few years. I installed with a swap partition a few months ago on the same computer. I have yet to see any measurable difference.

---

### Post by haqking on 2011-07-19
> **TheNosh said:**
> [http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux#Performance](http://en.wikipedia.org/wiki/Comparison_of_Windows_and_Linux#Performance)

Read this. Basically, swap partition are of little use on desktops. And Windows has had intelligent block allocation on NTFS since XP.

Also, a simple de-fragmentation, if done semi-regularly, should take very little time.

I ran Linux with no swap partition or swap file for a few years. I installed with a swap partition a few months ago on the same computer. I have yet to see any measurable difference.

your link under the memory management comparison says the same things i said.

And i never said that swap is needed, my machine doesnt use swap except for hibernation.

My point was to the OP that a flash will not improve things and in general in terms of use of RAM i believe Linux to be more efficient (though that wouldnt be noticed much with a desktop)

---

