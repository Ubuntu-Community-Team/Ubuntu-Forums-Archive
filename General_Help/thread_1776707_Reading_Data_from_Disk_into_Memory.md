---
title: "Reading Data from Disk into Memory"
date: 2011-06-06
forum: General Help
---

### Post by whchapman on 2011-06-06
I have a simple C program that reads a 1 GB file from disk into memory.
 
The first time I run this program, the process takes several seconds. But if I run this program again immediately after it finishes, the read happens almost instantly. What is going on here?
 
My suspicion is that the operating system is realizing that the data I'm trying to read is still uncorrupted in memory (its been freed but not overwritten), so instead of reading it again, it just gives me the same block. I would really like to know what this process is called, or any Googleable keywords that would allow me to research it.
 
The reason I ask is because the size of my input data has increased. Now I need to read in a 6 GB file (my system has 12 GB of RAM), but I'm not observing the same behavior with the larger file. Each time I run the program the read takes an equally long time. 
 
Any help will be greatly appreciated,
Bill
 
(Using Ubuntu Natty Narwhal 11.04)

---

### Post by mcduck on 2011-06-06
Linux kernel uses the part of RAM that isn't used for anything else to cache recently accessed data. This is why after running for some time almost all of the memory will be in some use. You can run "free -m" in a terminal to check your memory usage and amount of data that's used for buffers or cache. Read the *+/- buffers/cache* -line to see the amount of memory used by the OS and running programs, and how much is still available for them. From any program's point of view the memory sued as cache still counts as free, as cached data is simply dropped if a program needs more memory.

Also most modern hard drives have built-in cache that in the same way stores recently accessed data to avoid having to seek and read it from the disc again.

I would guess that the 1GB file fits into cache, while the kernel determines the 6GB file too big to be cached based on the available amount of memory and the recent usage of other files kept in cache at the moment. I could be wrong, though, the kernel memory management seems to be rather complicated business. :D

---

### Post by whchapman on 2011-06-07
Thank you for the reply. Based on your response I am confident the 1 GB of data was being cached by the OS, but the 6 GB data was not. I researched the issue but could not determine why the OS was deciding 6 GB was too large when I have over 11 GB of free memory.
 
Instead, I implemented a workaround to imitate the behavior of the cache. In my opinion, this workaround is superior to an actual solution since it gives me more direct control of what is in memory and what is not. Nonetheless, if anyone can explain how the cache algorithm works, I'd appreciate it for the sake of completing this thread.
 
My workaround uses a daemon process which loads the 6 GB file into a shared memory block using the shmget and shmat functions. My C program then uses those functions to get a pointer to the already-loaded block of memory.
 
Note that I had to increase the kernel shared memory limit from 32 MB to 7 GB in order for this to work. I did this by adding the following two lines to /etc/sysctl.conf and rebooting.
 
kernel.shmmax = 7340032000 <-- sets the total limit to 7 GB
kernel.shmall = 7340032000 <-- sets the per process limit to 7 GB
 
A good tutorial on using shared memory in C programs is here:
 
[http://www-personal.washtenaw.cc.mi.us/~chasselb/linux275/ClassNotes/ipc/shared_mem.htm](http://www-personal.washtenaw.cc.mi.us/~chasselb/linux275/ClassNotes/ipc/shared_mem.htm)

---

