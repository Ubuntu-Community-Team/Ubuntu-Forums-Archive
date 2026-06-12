---
title: "available memory Lucid Lynx"
date: 2011-07-06
forum: General Help
---

### Post by yirgacheffe on 2011-07-06
Hi, I am trying to run a (Java) program where I can specify how much memory I am allocating to it.

System monitor tells me that I am using:
Memory: 1000.5 MiB (6.2%) of 15.8 GiB
Swap: 2.2 MiB (0.0) of 5.6 GiB
- so it seems I have lots of free memory

Top tells me:


Mem:  16528264k total, 15561168k used,   967096k free,   212464k buffers
Swap:  5862392k total,     2216k used,  5860176k free, 14322932k cached

- how much is free, how much is used? Contradicting sytem monitor?

Now, if I want to run my program (a java application), I can only run it with a maximum of 2600 MB memory....at 2700 MB memory usage startup attempt, i have the following error message:


Executing: ~/_insight --memMax=2700
>> Error occurred during initialization of VM
>> Could not create the Java virtual machine.
>> Could not reserve enough space for object heap

I really want to run my program to use 5000 or 7000 MB of memory....


thanks
Sid

---

### Post by Gyokuro on 2011-07-06
I think with that amount of RAM you are using a 64 Bit edition and a 64 Bit JDK? Try to start your app via 

java -Xmx8500m yourapp

as your posted error message indicates that heap size is larger than your computer's physical memory (you have 16GB).

---

### Post by yirgacheffe on 2011-07-06
Thanks.
The machine is an AMD 64bit Opteron. The operating system is 32bit though, and program in question is also a 32 bit version.
I understand that the error message states that the heap size is larger than the physical memory....but why is that? Doesn't my program sees all 16 GB memory? 

By executing **java -Xmx8500m insight** I get the same error message:

Error occurred during initialization of VM
Could not reserve enough space for object heap
Could not create the Java virtual machine.

The error only goes away if I use Xmx2600 again.....

It is not a big deal, the program is working well, but to make it faster (as I work with big datasets) I thought I could use more of the available memory.
thanks

---

### Post by Azdour on 2011-07-06
Hi,

I believe that on a 32 bit operating system Xmx has a limit, I have not found the precise limit for Ubuntu. As far as I know the only way to use more is to have a 64 bit operating system.

---

### Post by yirgacheffe on 2011-07-06
Thanks,

I have Physical Address Extension (PAE) installed, this should take care of the limitations. If I read it well, without this the limit would be 2G...
thanks

---

### Post by yirgacheffe on 2011-07-06
Thanks,

I have Physical Address Extension (PAE) installed, this should take care of the limitations. If I read it well, without this the limit would be 2G...
thanks

---

### Post by Gyokuro on 2011-07-06
> **Azdour said:**
> Hi,

I believe that on a 32 bit operating system Xmx has a limit, I have not found the precise limit for Ubuntu. As far as I know the only way to use more is to have a 64 bit operating system.

Correct - it's an JVM switch but in the OP's case the 

limiting factor is the 32-Bit JVM and he/she should use a 64-Bit Ubuntu Edition and 64-Bit jdk to use that amount of memory for this hungry memory app - Oracle documented it here: 
[http://www.oracle.com/technetwork/java/hotspotfaq-138619.html#gc_heap_32bit](http://www.oracle.com/technetwork/java/hotspotfaq-138619.html#gc_heap_32bit)

---

### Post by yirgacheffe on 2011-07-06
Thanks everyone.

---

