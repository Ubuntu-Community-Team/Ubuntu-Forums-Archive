---
title: "Swap hard to ram"
date: 2011-02-18
forum: General Help
---

### Post by Cha0sBG on 2011-02-18
So i've found this little FAQ [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq)

I've done what it said and i think it works. But one thing came up to my mind: So i got a nice 512GB hard drive and 2GB ram. I've added 2GB of swap so that must make my ram = 4GB?. And i was wondering could i make it like 8GB cuz i'll be running a machine on a virtual box so i wanted more ram to handle everything. Any suggestions, tips or any help in general would be great. Thank you.

---

### Post by Asmodai on 2011-02-18
You can add as much swap as you want, but it will not be of much use.
Hard disks are several thousand times slower (as with swapping, seek times matter a great deal) than RAM. Once your 2 GB are full, parts of the RAM are moved to the swap space.
When they're needed, they're moved back to RAM, each operation taking significant amounts of time.
You can try to run so many applications that 4 GB of memory are used. You'll see that your system will become entirely unusable.

---

### Post by Cha0sBG on 2011-02-18
So what your saying is it gives a little improvement but i can't expect that great of results, is that correct ?

---

### Post by Asmodai on 2011-02-18
Depends on what you would call an improvement.
If you don't have swap and you reach 2 GB RAM usage, the system will run out of memory and will kill a process (usually the one with the highest RAM usage). If you do have swap, the system will start swapping. So the speed of your system will slow down to a crawl, but no processes are killed.

---

