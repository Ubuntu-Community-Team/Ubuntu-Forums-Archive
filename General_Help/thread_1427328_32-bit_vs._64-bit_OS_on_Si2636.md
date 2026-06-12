---
title: "32-bit vs. 64-bit OS on Si2636"
date: 2010-03-11
forum: General Help
---

### Post by nukleuzN on 2010-03-11
Hi,

My computer seems to work really slow - after installing Ubuntu 9.10. Facebook (and other sites with much JS/Ajax), Photoshop, Flash, Java etc is specially making troubles for me.

Now when I installed this add-on "User agent switcher" in FF I found out that I have been using 32-bit OS on this computer - witch actually is a 64-bit PC. (FSC Si2636)

Could this be the answer to my coumputer works so slowly? :/ Would my computer work faster with a 64-bit OS - or opposite? 

My fan is really crazy...!

---

### Post by dcstar on 2010-03-11
> **nukleuzN said:**
> 
Could this be the answer to my coumputer works so slowly? :/ Would my computer work faster with a 64-bit OS - or opposite? 


Maybe, but you should probably wait until 10.04 is released.

BTW, update your forum profile, it says 7.10.

---

### Post by Vaphell on 2010-03-11
64 vs 32 is pretty much negligible - it's better to use 32 when your system is relatively low on ram (more efficient allocation of data in memory) but if you have 4GB or more you definitely should use 64bit. Some heavy number crunching apps take advantage of 64bit mode but it's not groundbreaking difference and 32bit is more tested and stable (flash10 64 for example is in alpha stage but it works ok).

what does **top** launched in terminal say?
is your cpu heavily taxed by something?
maybe some problem with performance/energy management, cpu overheats easily and is throttled to lower frequency to cool down? that would explain awful performance.

---

### Post by 3rdalbum on 2010-03-11
Computer going slowly usually means "a program has gone crazy and is using all your CPU power". You've mentioned the fan going at high speed, so that confirms it. Use the System Monitor to find out what program is using the most CPU%, and kill that program.

32-bit and 64-bit:

A 64-bit operating system will run slightly faster, but you might not be able to notice a speed difference between the two. 64-bit doesn't mean "twice the speed of 32-bit", it's a reference to the size of numbers that the computer can deal with in one clock cycle. If you're doing something that uses 64-bit numbers, you'll see a speed improvement. If you have more than 3 GiB of RAM, then a 64-bit operating system will be able to address all that memory, because it will be using the longer 64-bit memory addresses.

---

### Post by El Zoido on 2010-03-12
I have to agree, unless you have 4GB ram or more I would stay with 32bit.

As you mentioned your fan going at high speed, could it be that it needs some cleaning?
Did you have problems like freezes or crashes recently?
This could also point to a problem with overheating.

---

### Post by nukleuzN on 2010-03-13
> **Vaphell said:**
> what does **top** launched in terminal say?
```
Tasks: 166 total,   3 running, 163 sleeping,   0 stopped,   0 zombie
Cpu(s):  3.1%us,  1.6%sy,  0.0%ni, 95.2%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2048752k total,  1223296k used,   825456k free,    89876k buffers
Swap:  6000236k total,        0k used,  6000236k free,   453348k cached

```

> **3rdalbum said:**
> Computer going slowly usually means "a program has gone crazy and is using all your CPU power". You've mentioned the fan going at high speed, so that confirms it. Use the System Monitor to find out what program is using the most CPU%, and kill that program.
Hmmm... Its instant. Specially when i use Firefox. As I remember my PC wasnt like this before. Maybe I need a new one.

> **El Zoido said:**
> I have to agree, unless you have 4GB ram or more I would stay with 32bit.

As you mentioned your fan going at high speed, could it be that it needs some cleaning?
Did you have problems like freezes or crashes recently?
This could also point to a problem with overheating.
- No crashes
- No program freeze
- Did re-install this computer for a month ago - then it was 32-bit. Yesterday I re-installed again, but this time 64. Cant notice any difference :(

---

