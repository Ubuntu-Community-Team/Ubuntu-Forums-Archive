---
title: "memory"
date: 2009-09-21
forum: General Help
---

### Post by hotashes02 on 2009-09-21
[B]ubuntu only shows half of memory how I can fix it?
I have 2 memory of 256mb
and only 371.2mb is recognize
[/B]

---

### Post by hotashes02 on 2009-09-21
Anyone?

---

### Post by Warren Watts on 2009-09-21
Is any of your RAM shared with onboard video?

---

### Post by hotashes02 on 2009-09-21
> **Warren Watts said:**
> Is any of your RAM shared with onboard video?
how i check if my RAM shared memory with onboard video?

---

### Post by MegaLoler on 2009-09-21
> **hotashes02 said:**
> [B]ubuntu only shows half of memory how I can fix it?
I have 2 memory of 256mb
and only 371.2mb is recognize
[/B]

It says 371.2 Mib not Mb, I don't know the difference, but i think one is more bytes than the other, but i don't know for sure.

---

### Post by Warren Watts on 2009-09-21
> **hotashes02 said:**
> how i check if my RAM shared memory with onboard video?

Perhaps we need more information.

First of all, where did you get the 371.2mb number from?  What program or resource provided you with that number?

What do you get when you type **free** into terminal? In the sample below, you can see that my PC is reporting 512MB RAM (515980KB)
```
warren@server-550:~$ free
             total       used       free     shared    buffers     cached
Mem:        515980     472564      43416          0     117976     271292
-/+ buffers/cache:      83296     432684
Swap:       481940      59768     422172

```



What does lshw report in regards to your memory? ( type **sudo lshw -short | grep memory** into the  terminal)  In the sample below, you can see that lshw is reporting  512MB system memory, composed of (2) 128MB sticks and (1) 256MB stick, with one emply DIMM slot.
```
warren@server-550:~$ sudo lshw -short | grep memory
/0/0                                 memory      128KB BIOS
/0/4/a                               memory      32KB L1 cache
/0/4/b                               memory      512KB L2 cache
/0/1f                                memory      512MB System Memory
/0/1f/0                              memory      128MB DIMM EDRAM
/0/1f/1                              memory      128MB DIMM EDRAM
/0/1f/2                              memory      256MB DIMM EDRAM
/0/1f/3                              memory      DIMM EDRAM [empty]

```

---

### Post by hotashes02 on 2009-09-22
> **Warren Watts said:**
> Perhaps we need more information.

First of all, where did you get the 371.2mb number from?  What program or resource provided you with that number?

What do you get when you type **free** into terminal? In the sample below, you can see that my PC is reporting 512MB RAM (515980KB)
```
warren@server-550:~$ free
             total       used       free     shared    buffers     cached
Mem:        515980     472564      43416          0     117976     271292
-/+ buffers/cache:      83296     432684
Swap:       481940      59768     422172

```What does lshw report in regards to your memory? ( type **sudo lshw -short | grep memory** into the  terminal)  In the sample below, you can see that lshw is reporting  512MB system memory, composed of (2) 128MB sticks and (1) 256MB stick, with one emply DIMM slot.
```
warren@server-550:~$ sudo lshw -short | grep memory
/0/0                                 memory      128KB BIOS
/0/4/a                               memory      32KB L1 cache
/0/4/b                               memory      512KB L2 cache
/0/1f                                memory      512MB System Memory
/0/1f/0                              memory      128MB DIMM EDRAM
/0/1f/1                              memory      128MB DIMM EDRAM
/0/1f/2                              memory      256MB DIMM EDRAM
/0/1f/3                              memory      DIMM EDRAM [empty]

```

I geting the 371.2mb from the system monitor

**from free** in the terminal i get 
```
             total       used       free     shared    buffers     cached
Mem:        380108     329104      51004          0      21040      89984
-/+ buffers/cache:     218080     162028
Swap:      4607992     182024    4425968

```**from sudo lshw -short | grep memory **in the terminal i get 
```
/0/0                            memory         128KiB BIOS
/0/4/8                          memory         128KiB L1 cache
/0/4/9                          memory         128KiB L2 cache
/0/21                           memory         512MiB System Memory
/0/21/0                         memory         256MiB DIMM DDR 333 MHz (3.0 ns)
/0/21/1                         memory         256MiB DIMM DDR 333 MHz (3.0 ns)
```

---

### Post by P4man on 2009-09-22
99.99% sure you have onboard video that is using 128 MB of your ram. If you go in to the BIOS, you can probably reduce that to 64 or 32 which is probably a better compromise.

---

### Post by CatKiller on 2009-09-22
> **P4man said:**
> 99.99% sure you have onboard video that is using 128 MB of your ram.

Actually, I think your confidence level should be lower than that. The other likely culprit is a motherboard that can't handle the memory density of one of the sticks in there. That was a pain with computers of that vintage. The symptom would be only half the memory of the affected sticks being detected. You'd need to see what the BIOS reported as available memory to be sure.

---

### Post by P4man on 2009-09-22
> **CatKiller said:**
> Actually, I think your confidence level should be lower than that. The other likely culprit is a motherboard that can't handle the memory density of one of the sticks in there. That was a pain with computers of that vintage. The symptom would be only half the memory of the affected sticks being detected. You'd need to see what the BIOS reported as available memory to be sure.

His lsw output shows 2x256Mb, so his bios see that too.
Anyway, I'll concede you a point, and reduce my confidence level to 99.9% :)

---

### Post by CatKiller on 2009-09-22
> **P4man said:**
> His lsw output shows 2x256Mb, so his bios see that too.

Good point. I hadn't spotted that.

> Anyway, I'll concede you a point, and reduce my confidence level to 99.9% :)

:D

---

### Post by hotashes02 on 2009-09-23
> **P4man said:**
> 99.99% sure you have onboard video that is using 128 MB of your ram. If you go in to the BIOS, you can probably reduce that to 64 or 32 which is probably a better compromise.
thanks thanks now i have 466mb

---

