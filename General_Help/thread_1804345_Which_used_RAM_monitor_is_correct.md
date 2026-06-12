---
title: "Which used RAM monitor is correct"
date: 2011-07-14
forum: General Help
---

### Post by mastablasta on 2011-07-14
I had to remove Xubuntu desktop and went back to pure gnome. Using 10.04 on this computer.

The whole thing started to work very very slow. Anyway back in gnome i get these readings in free -m command:

```
             total       used       free     shared    buffers     cached
Mem:           228        226          2          0         10         86
-/+ buffers/cache:        129         99
Swap:          668          1        667
```

the i used top command and go this:
```
top - 21:49:36 up 4 min,  2 users,  load average: 0.86, 1.02, 0.48
Tasks: 155 total,   1 running, 154 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.9%us,  4.6%sy,  0.0%ni, 83.2%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    234476k total,   224660k used,     9816k free,    11596k buffers
Swap:   685048k total,     2152k used,   682896k free,    82564k cached
```

Finnaly i tried the system monitor and it said

Memory:126.6 MiB (55,3%) of 229 MiB 
Swap: 2.1 MiB (0.03%) of 669 MiB

Yesterday memory was below 100. so which one is true and which one is lying?

System now otherwise works fine. Quite fast actually even with more programmes open.

---

### Post by mastablasta on 2011-07-15
bump, before this falls into oblivion again.

---

### Post by shad0w_walker on 2011-07-15
The actually in use right now measurement is the second row, used. The first row shows all memory usage, including caches, which are used to speed up accessing recently opened files and the like. The actual RAM in use by your programs and the system is in the second row. This is shown without caches including and just what is actively used by the OS and programs.

---

