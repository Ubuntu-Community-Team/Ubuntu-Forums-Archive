---
title: "Keyboard Input Lagging"
date: 2010-12-12
forum: General Help
---

### Post by Nexusx6 on 2010-12-12
Hello,

I'm running Kubuntu 10.4 and I'm experiencing an issue in which at seemingly random points Kubuntu will start lagging at receiving typed keystrokes. An example of this would be:

```
Typed: The quick brown fox jumped over the lazy dog
Shown: The quik rown fox jumpe over he lay dog

```

The lag is actually visible, I can watch the cursor try to catch up my keystrokes. If I type slow enough it will catch every key, but typing to fast causes letters to be missed like in he above example.

In System Monitor, the Process Table doesn't show any specific program eating up an usual amount of resources, typically Xorg bobbling up and down around 5%, Firefox between 1 and 3%. The System Load graph, however, shows spikes of activity from %15 to 30% every few seconds, though I'm not sure if any of this is relevant.

The only way to fix the issue right now is to restart my computer :| So I'd really appreciate any help.

```

top - 12:36:22 up  3:27,  1 user,  load average: 0.38, 0.36, 0.37
Tasks: 158 total,   1 running, 156 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.3%us,  0.7%sy,  0.0%ni, 97.0%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2056720k total,  1317480k used,   739240k free,   138672k buffers
Swap:  1951856k total,       76k used,  1951780k free,   498232k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                                                                                                               
 2835 fox       20   0  9144 1228  816 S   31  0.1   0:03.71 ksysguardd                                                                                                                                                                            
 1010 root      20   0  155m  67m  15m S    3  3.4   9:40.28 Xorg                                                                                                                                                                                  
 2833 fox       20   0  458m  38m  18m S    2  1.9   0:36.96 ksysguard                                                                                                                                                                             
 1643 fox       20   0  322m  42m  16m S    1  2.1   0:01.10 yakuake                                                                                                                                                                               
 1575 fox       20   0  661m  69m  41m S    1  3.5   5:50.61 kwin                                                                                                                                                                                  
 2856 fox       20   0  627m 177m  29m S    1  8.9   1:21.00 firefox-bin                                                                                                                                                                           
 2894 fox       20   0 67260  16m  10m S    1  0.8   0:06.26 npviewer.bin                                                                                                                                                                          
 3022 fox       20   0 19224 1436 1044 R    0  0.1   0:00.10 top                                                                                                                                                                                   
    1 root      20   0 23784 1964 1272 S    0  0.1   0:00.48 init

```

---

