---
title: "Freeing up memory and seeing whats using it?"
date: 2010-04-24
forum: General Help
---

### Post by HHx66 on 2010-04-24
I have Xubuntu installed, and I still end up using around 550-720MB RAM? Does Linux handle memory differently than Windows? Things are still quick, it just seems a bit high, how can I tell whats using memory and kill services and stuff that aren't needed?

---

### Post by blueridgedog on 2010-04-24
Linux caches items in memory, as empty memory is essentially wasted.  The objective is to use the memory you have efficiently.

What is the ouput of 

```
free
```

If you are not using swap, then you are fine.

You can see what is using memory by running the "top" command then typing "M" (note capital M) to sort by memory.

---

### Post by wojox on 2010-04-24
Show top 10 Memory Consuming Process:

```
ps auxf | sort -nr -k 4 | head -10
```

---

### Post by HHx66 on 2010-04-24
The top command shows:

```
             total       used       free     shared    buffers     cached
Mem:       1023612     797264     226348          0         52     106200
-/+ buffers/cache:     691012     332600
Swap:      2000052     145600    1854452

```

---

### Post by QIII on 2010-04-24
There should be some detail down below what you have given us there.  That's a summary.

Run top again, then click ctrl-C to stop the updating.  Cut and paste the whole thing back here.

---

### Post by blueridgedog on 2010-04-25
Also, hit "M" while running top to sort by memory usage.

---

### Post by HHx66 on 2010-04-25
Ah alright sorry, I posted the results of free instead.

Heres the top command:

```
top - 14:34:10 up 13:43,  2 users,  load average: 0.49, 0.22, 0.08
Tasks: 151 total,   2 running, 149 sleeping,   0 stopped,   0 zombie
Cpu(s): 43.4%us,  3.3%sy,  0.0%ni, 53.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1023612k total,  1013424k used,    10188k free,        8k buffers
Swap:  2000052k total,    75452k used,  1924600k free,   437284k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
23629 ~username  20   0  122m  37m  14m R 33.5  3.8   1:05.07 npviewer.bin       
 1182 root      20   0  347m 108m  18m S  7.3 10.8 312:30.70 Xorg               
 4122 ~username  20   0  632m  96m  22m S  2.0  9.6   6:59.85 chrome             
23573 ~username  20   0  871m  40m  13m S  1.0  4.0   0:02.74 chrome             
 1999 ~username  20   0  206m  14m 8728 S  0.7  1.4   4:41.21 xfce4-systemloa    
 2001 ~username  20   0  165m 8512 7096 S  0.7  0.8   2:04.86 xfce4-netload-p    
23715 ~username  20   0 19132 1344  980 R  0.7  0.1   0:00.22 top                
 1944 ~username  20   0  232m  13m 8848 S  0.3  1.4   1:13.86 xfce4-panel        
23610 ~username  20   0  239m  14m  12m S  0.3  1.5   0:00.95 chrome             
23678 ~username  20   0  182m  15m 9.8m S  0.3  1.6   0:00.60 xfce4-terminal     
    1 root      20   0 19432 1508 1044 S  0.0  0.1   0:00.49 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.01 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.39 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0         
    6 root      15  -5     0    0    0 S  0.0  0.0   0:00.06 events/0           
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset     
```

thats the FULL display, I edited out my username as I'm paranoid about that stuff, but other than that thats it exactly.

---

### Post by blueridgedog on 2010-04-25
Your system appears to be running OK for one with a single gig of ram.  Very little is being swapped.  The only thing I see off hand is Chrome creates a new process for each tab.  Perhaps you can try closing unused tabs - or switching to a web browser that has a smaller footprint.

You can kill a process once you see the PID in top with the command:

```
kill -9 PID
```

Replace PID with the numerical process ID.  Typically that is not needed as you can simply close the program unless it is non-responsive.

---

### Post by HHx66 on 2010-04-25
Yeah, I've been meaning to put another GB into this system just haven't had the chance. I might try out Firefox again (it's been a long time since I have).

---

### Post by The Real Dave on 2010-04-25
The output of 

```
free -m
```

will resolve the RAM usage to MB and make a tad more sense :)

---

