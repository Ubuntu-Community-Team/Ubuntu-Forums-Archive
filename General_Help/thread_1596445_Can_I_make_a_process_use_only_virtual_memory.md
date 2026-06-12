---
title: "Can I make a process use only virtual memory?"
date: 2010-10-14
forum: General Help
---

### Post by johnkills on 2010-10-14
I understand that in linux virtual memory would be the same as swap and I also understand that linux only uses swap when your computer has used all your pc memory. I hope both assumption are right. Anyway.. 

Can I make a process like firefox use **ONLY** virtual memory/swap? No access to RAM.

Thanks :)

---

### Post by lloyd_b on 2010-10-14
> **johnkills said:**
> I understand that in linux virtual memory would be the same as swap and I also understand that linux only uses swap when your computer has used all your pc memory. I hope both assumption are right. Anyway.. 

Can I make a process like firefox use **ONLY** virtual memory/swap? No access to RAM.

Thanks :)

Your understanding of "virtual memory" is a bit off.  

In order for a program to run, it *must* be in RAM.  What "virtual memory" does is create the illusion that the machine actually has more memory than it has physical RAM.  

It does this by moving the memory from processes from RAM onto disk (swap space), so that the RAM it was occupying can be used by another process.  When there is a demand for that virtual memory again, it is "swapped" back into RAM, with something else being swapped out to disk in its place.

So you cannot "create a process in virtual memory" - everything running on the computer is *already* inside the virtual memory system, except for certain portions of the kernel.  Sections of virtual memory are swapped between physical RAM and disk as needed, so that the maximum amount of RAM is available to processes that need it.

Lloyd B.

---

### Post by johnkills on 2010-10-14
> **lloyd_b said:**
> 
In order for a program to run, it *must* be in RAM.  What "virtual memory" does is create the illusion that the machine actually has more memory than it has physical RAM.  

Why it **must** be in RAM? Can I make the illusion to the program so it think when it starts that it already has no RAM to work?  Therefore, it will work only from "virtual memory".

---

### Post by d5xtgr on 2010-10-14
To my understanding, the swap space can hold data but not work with it in the same way that true RAM can- so if you have a process not doing anything at the moment, just statically taking up RAM, you can bump it to swap and free up the RAM for something that would use it.  If you want to use more RAM than you have, the tasks need to queued up.
This is based on research I did when I accidentally dissociated my swap from my OS- if I have said something incorrect or inaccurate please correct me.

---

### Post by d5xtgr on 2010-10-14
If you want the process to be more readily bumped to swap when it goes inactive, you can increase the 'vm.swappiness' value in etc/sysctl.conf, which you will need to edit with sudo or similar; you still won't be able to run processes in it, though.  For more details, go to [https://help.ubuntu.com/community/SwapFaq](https://help.ubuntu.com/community/SwapFaq).  Swap is just about equivalent to the page file on Windows systems, if that helps you conceptualize it.

---

### Post by lloyd_b on 2010-10-14
> **johnkills said:**
> Why it **must** be in RAM? Can I make the illusion to the program so it think when it starts that it already has no RAM to work?  Therefore, it will work only from "virtual memory".

The processor in your computer cannot execute instructions or alter memory locations unless those instructions/memory locations are in physical RAM.  

Consider this analogy - Imagine there is a guy sitting at a desk.  He has lists of instructions that he has to perform, and files on which he has to perform these instructions.  He only has a limited amount of desk space, so he's been given a file cabinet to hold any files that he doesn't actually need at the moment.

The guy represents the processor in your computer.  His "desk" is RAM.  His "filing cabinet" is swap space.  Now he can have a huge "virtual desk" (virtual memory space), depending on how big that file cabinet is.  But in order for him to actually do anything with a file, he must first pull it out of the file cabinet and put it on his desk (swap from disk to RAM).

You can potentially push all of a process into swap space.  But it cannot execute from there - it has to be swapped back into RAM in order to run.

Lloyd B.

---

### Post by johnkills on 2010-10-14
I get it, it makes sense. 

Thanks everyone :)

---

