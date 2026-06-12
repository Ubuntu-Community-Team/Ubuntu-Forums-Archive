---
title: "Boinc, GPU and task priority"
date: 2011-04-15
forum: General Help
---

### Post by HankB on 2011-04-15
I'm running two Boinc distributed projects. One (Rosetta) uses the CPU cores and gets near 100% of each on a four core system. The other (GPUGRID) uses an nvidia GPU and is presently starved for CPU cycles.

While Rosetta is enabled, this is what I see:

```
hbarta@olive:~$ top -n 1

top - 11:59:54 up 18:29,  5 users,  load average: 5.15, 5.46, 5.40
Tasks: 251 total,   7 running, 244 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.4%us,  0.6%sy, 97.2%ni,  0.5%id,  0.0%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   4057932k total,  4020360k used,    37572k free,    52612k buffers
Swap:  8000288k total,    20184k used,  7980104k free,  1078336k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
[B][COLOR="Red"]17736 boinc     39  19  447m 441m  400 R   98 11.1  24:18.51 minirosetta_2.1    
17737 boinc     39  19  440m 433m  624 R   98 10.9  24:20.91 minirosetta_2.1    
17738 boinc     39  19  453m 445m  304 R   98 11.2  24:25.14 minirosetta_2.1    
17735 boinc     39  19  437m 430m  368 R   89 10.9  24:13.27 minirosetta_2.1    [/COLOR][/B]
   41 root      20   0     0    0    0 S    2  0.0   0:03.56 ata/3              
 1908 root      20   0  156m  46m  15m S    2  1.2  20:03.41 Xorg               
 2265 hbarta    20   0  294m  39m  13m S    2  1.0   5:49.05 compiz             
 2398 hbarta    20   0  299m  25m  14m S    2  0.6  16:20.79 boincmgr           
 8431 hbarta    20   0  208m  22m  11m S    2  0.6   0:07.46 gnome-terminal     
[COLOR="red"][B] 8886 boinc     30  10  166m  90m  32m R    2  2.3   1:54.67 acemd2_6.13_x86    
[/B][/COLOR]13624 hbarta    20   0  537m  92m  32m S    2  2.3   1:30.03 chromium-browse    
13967 hbarta    25   5  876m  79m  22m S    2  2.0   1:04.08 chromium-browse    
16389 hbarta    25   5  906m  99m  20m S    2  2.5   1:00.22 chromium-browse    
18396 hbarta    20   0  862m  66m  26m S    2  1.7   0:17.94 chromium-browse    
{zero CPU users deleted}
       
hbarta@olive:~$ nvidia-smi -a 

==============NVSMI LOG==============


Timestamp			: Fri Apr 15 12:00:35 2011

Driver Version			: 260.19.29


GPU 0:
	Product Name		: GeForce GTX 460
	PCI Device/Vendor ID	: e2210de
	PCI Location ID		: 0:1:0
	Board Serial		: 650381377
	Display			: Connected
	Temperature		: 53 C
	Fan Speed		: 26%
	Utilization
	    GPU			: 8%
	    Memory		: 1%
hbarta@olive:~$
``` 

If I suspend Rosetta, GPUGRID gets enough CPU to keep the GPU relatively busy:


```
hbarta@olive:~$ top -n 1

top - 12:01:19 up 18:31,  5 users,  load average: 5.69, 5.55, 5.44
Tasks: 235 total,   1 running, 234 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.4%us,  0.7%sy, 97.2%ni,  0.5%id,  0.0%wa,  0.1%hi,  0.1%si,  0.0%st
Mem:   4057932k total,  2219820k used,  1838112k free,    48924k buffers
Swap:  8000288k total,    20288k used,  7980000k free,  1074920k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                   
[B][COLOR="Red"] 8886 boinc     30  10  166m  90m  32m S    8  2.3   1:56.26 acemd2_6.13_x86           
[/COLOR][/B] 1908 root      20   0  156m  46m  15m S    6  1.2  20:07.18 Xorg                      
 2265 hbarta    20   0  294m  39m  13m S    2  1.0   5:50.29 compiz                    
 2334 hbarta    20   0  215m 9380 7096 S    2  0.2   2:55.87 multiload-apple           
 2398 hbarta    20   0  299m  25m  14m S    2  0.6  16:22.21 boincmgr                  
 8431 hbarta    20   0  208m  22m  11m S    2  0.6   0:08.33 gnome-terminal            
13624 hbarta    20   0  537m  92m  32m S    2  2.3   1:31.34 chromium-browse           
13721 hbarta    20   0  270m  87m  20m S    2  2.2   2:25.03 npviewer.bin              
16389 hbarta    25   5  906m 100m  20m S    2  2.5   1:01.81 chromium-browse           
20289 hbarta    20   0 19352 1372  928 R    2  0.0   0:00.03 top                                            
{zero CPU users deleted}

hbarta@olive:~$ nvidia-smi -a 

==============NVSMI LOG==============


Timestamp			: Fri Apr 15 12:01:32 2011

Driver Version			: 260.19.29


GPU 0:
	Product Name		: GeForce GTX 460
	PCI Device/Vendor ID	: e2210de
	PCI Location ID		: 0:1:0
	Board Serial		: 650381377
	Display			: Connected
	Temperature		: 57 C
	Fan Speed		: 34%
	Utilization
	    GPU			: 91%
	    Memory		: 12%
hbarta@olive:~$
``` 

I would have thought that the higher nice setting for the Rosetta tasks would allow the GPUGRID sufficient CPU cycles to keep the GPU busy w/out sacrificing much Rosetta performance but that seems not to be the case. Is there any tweak I can apply to the scheduling priority to make these share resources better?

This is on:
```
hbarta@olive:~$ cat /etc/issue
Ubuntu 10.04.2 LTS \n \l

hbarta@olive:~$ uname -a
Linux olive 2.6.32-30-generic #59-Ubuntu SMP Tue Mar 1 21:30:46 UTC 2011 x86_64 GNU/Linux
hbarta@olive:~$
``` 


thanks,
hank

---

