---
title: "very high memory usage"
date: 2010-01-23
forum: General Help
---

### Post by nitstorm on 2010-01-23
hi all, 

jus wondering why so much of the RAM is getting used on my machine now. it's pretty ok when the system starts and jus keeps increasing and in a short while about 96% of my RAM starts getting used up.. should i be worrying or something?? also jus bugging me why so much of my RAM is getting used
This is my free -m output:
```

   total       used       free     shared    buffers     cached
Mem:          2003       1937         66          0        516        788
-/+ buffers/cache:        632       1371
Swap:          972          0        972

```
and this is my top output
```

top - 14:34:30 up  2:22,  2 users,  load average: 0.23, 0.13, 0.10
Tasks: 149 total,   2 running, 147 sleeping,   0 stopped,   0 zombie
Cpu(s): 21.1%us,  6.3%sy,  0.0%ni, 72.3%id,  0.0%wa,  0.2%hi,  0.2%si,  0.0%st
Mem:   2051212k total,  1987612k used,    63600k free,   528244k buffers
Swap:   995988k total,        0k used,   995988k free,   813476k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1797 nits      20   0  557m 144m  32m S   29  7.2  25:03.37 firefox            
  909 root      20   0 67304  22m  13m S   16  1.1  14:08.05 Xorg               
 1577 nits      20   0  285m 6164 4964 S    7  0.3   4:27.29 pulseaudio         
 2697 nits      20   0 14908 3384 1920 S    3  0.2   1:19.53 conky              
 2763 nits      20   0  174m  63m  22m S    1  3.1   2:03.89 vlc                
 2979 nits      20   0 37996  12m 9556 S    1  0.6   0:01.13 gnome-terminal     
 1687 nits      20   0 79224  25m 9132 S    0  1.3   1:20.80 compiz.real        
 1754 nits      20   0 29940  16m 3920 S    0  0.8   0:14.57 ubuntuone-syncd    
 3086 nits      20   0  2472 1180  884 R    0  0.1   0:00.10 top                
    1 root      20   0  2636 1532 1128 S    0  0.1   0:00.90 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.08 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.04 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      15  -5     0    0    0 S    0  0.0   0:00.08 events/0  

```

Thanks for the help in advance, cheers :)

---

### Post by d3v1150m471c on 2010-01-23
How much RAM do you have?

---

### Post by d3v1150m471c on 2010-01-23
I'm closing the tab on this thread. You can get back to me by private message if you like.

---

### Post by nitstorm on 2010-01-23
sorry for the lil late reply, had some trouble logging in. oh i have 2 gb of RAM

---

### Post by fjf314 on 2010-01-23
A simple thing would be to check which processes are eating up the most memory. I'm sure there is a CLI method for this, but I have no idea what it is. However, you should be able to open the System Monitor (System > Administration > System Monitor) and sort your Processes by memory usage, assuming that this isn't a server build.

---

### Post by d3v1150m471c on 2010-01-23
input this command and tell me what you get.
```

sysctl -q vm.swappiness && sysctl -q vm.vfs_cache_pressure

```

---

### Post by jbruced on 2010-01-23
Firefox looks a little high, maybe upgrade to 3.6.

Nothing looks that much to me?

Anyone else see anything extreme?

EDIT: Just took another look at mine. Looks like most of the memory is cached and is there just in case, not really being used, and won't affect anything if another process/application needs the memory, just keeps common stuff available quickly if needed, and just makes room for whatever is actually being used.

---

### Post by d3v1150m471c on 2010-01-23
> **jbruced said:**
> Firefox looks a little high, maybe upgrade to 3.6.

Nothing looks that much to me?

Anyone else see anything extreme?

Google chrome beta is available for linux and it hauls balls...If you want slightly less speed but more security then use swiftfox and enable the pipelining up to 8 tunnels. Look on google for tutorials for this. 

Also, Nitstorm, let me know what the above command says please.

---

### Post by nitstorm on 2010-01-23
This is the output i got for 
sysctl -q vm.swappiness && sysctl -q vm.vfs_cache_pressure
vm.swappiness = 60
vm.vfs_cache_pressure = 100

Firefox is high because i am buffering a video....

---

### Post by d3v1150m471c on 2010-01-23
Research this before you try it. swappiness and cache_pressure both range from 0 to 100. swappiness controls how aggressively your system uses RAM over swap space, cache_pressure how aggressively it stacks cache info into your RAM. swappiness - lower the number, the higher the RAM input. This is the same with cache_pressure. With 2 gigs of RAM you have more than decent room to play around with these and find out what works best. You can change them without making permanent changes via:
```

sudo sysctl -w vm.swappiness= && sudo sysctl -w vm.vfs_cache_pressure= && sudo sysctl -p 

```
*** you have to add a number ranging from 0 to 100 following the "=" character.

If you get a ratio that you like and want to make it permanent:

```

gksudo gedit /etc/sysctl.conf

```

Then, add at the very bottom of the file, **vm.swappiness = numbergoeshere** and/or **vm.vfs_cache_pressure = numbergoeshere**.

Note - the spaces are there intentionally. This is not an error.

example:
```

# Log Martian Packets
#net.ipv4.conf.all.log_martians = 1
#
# The contents of /proc/<pid>/maps and smaps files are only visible to 
# readers that are allowed to ptrace() the process
# kernel.maps_protect = 1
vm.swappiness = 10
vm.vfs_cache_pressure = 50

```

That is the setup on my machine and it runs very, very fast.
Toshiba Satellite L305 - Intel Dual Core 2.0ghz with 2.8mb RAM.

**IF YOU WANT TO USE HIBERNATE OR SOMETHING SIMILAR THEN DO NOT MAKE SWAPPINESS 0**

---

### Post by nitstorm on 2010-01-23
Thanks d3v1150m471c . Will try it out :)

---

### Post by OrangeCrate on 2010-01-23
> **nitstorm said:**
> hi all, 

jus wondering **why so much of the RAM is getting used on my machine** now. it's pretty ok when the system starts and jus keeps increasing and in a short while about 96% of my RAM starts getting used up.. **should i be worrying or something?**? also jus bugging me why so much of my RAM is getting used...

<snip>



This is probably the best article on Linux memory management that I've ever seen:

[http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management](http://www.gentoo-wiki.info/FAQ_Linux_Memory_Management)

It should answer most, if not all of your questions, and no, it's nothing to worry about.

---

### Post by happyhamster on 2010-01-23
> **nitstorm said:**
> hi all, 

jus wondering why so much of the RAM is getting used on my machine now. it's pretty ok when the system starts and jus keeps increasing and in a short while about 96% of my RAM starts getting used up.. should i be worrying or something?? also jus bugging me why so much of my RAM is getting used
This is my free -m output:
```

   total       used       free     shared    buffers     cached
Mem:          2003       1937         66          0        516        788
-/+ buffers/cache:        632       1371
Swap:          972          0        972

```

That means 632MB is being used, 66MB is unused, and the rest is cache/buffers (which RAM is available for applications should they demand it). Swap is unused, which is great.
In other words: there's more than enough RAM, and the system is using unused RAM as a cache to improve the responsiveness of the desktop (opening previously used applications or documents will go faster, etc).
You should only worry if the swap is being used a lot. 

Here's my desktop (after 2 days uptime):
```

user2@jaunty:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          7990       7699        290          0        160       6699
-/+ buffers/cache:        839       7150
Swap:         1921         16       1905

```

---

### Post by nitstorm on 2010-01-23
Wow thanks happyhamster, i jus read an article that *OrangeCrate *had suggested, and then my doubt was solved, was heading to mark this thread solved when i saw ur post. Thanks happyhamster :D 

Big thanks to *OrangeCrate, happyhamster* and *d3v1150m471c *and all the others for your help. THREAD SOLVED!!!

---

### Post by OrangeCrate on 2010-01-23
> **nitstorm said:**
> Wow thanks happyhamster, i jus read an article that *OrangeCrate *had suggested, and then my doubt was solved, was heading to mark this thread solved when i saw ur post. Thanks happyhamster :D 

Big thanks to *OrangeCrate, happyhamster* and *d3v1150m471c *and all the others for your help. THREAD SOLVED!!!

:)

---

