---
title: "wish8.4 - 100% CPU usage"
date: 2011-11-16
forum: General Help
---

### Post by k4rizma on 2011-11-16
Hello all, 

Thanks in advance for reading :)

I'm on ubuntu 10.10 and as the title says I have a process called wish8.4 that keeps pegging out my processor at close to 100%.  

I can kill the process but it restarts itself....so I'm looking for some advice. 


```

top - 08:26:03 up 10 min,  3 users,  load average: 1.08, 0.42, 0.23
Tasks: 144 total,   2 running, 140 sleeping,   0 stopped,   2 zombie
Cpu(s): 11.8%us,  6.1%sy,  0.4%ni, 77.1%id,  4.5%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   1025016k total,   530224k used,   494792k free,    90852k buffers
Swap:  1648636k total,        0k used,  1648636k free,   223428k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                      
 1722 jason     20   0 20300 7688 2696 R 93.9  0.8   1:03.91 wish8.4 


```

Obviously this is a bad thing. Any advice as to how I can keep this process killed or from pegging out my processor? 

Is it a service that starts up in this runlevel?   I cant remember where those files are kept or I would just go look myself >.<  Will google in the meantime but any help will be greatly appreciated. 

With Regards


ps this smiley rocks!  :lolflag:

---

### Post by Cæncel on 2011-11-16
wish8.5 (usr/bin/amsn) stands for aMSN process, you provably have problems regarding aMSN, try to uninstall it completely or use alternative clients, i suggest you Emesene, since Pidgin and Empathy have a bad quality in their latest releases (libpurple) (no avatar displaying, issues with chat text, transfers no working and making crash the program)

---

