---
title: "Fan on laptop went nuts and machine froze"
date: 2011-06-16
forum: General Help
---

### Post by Retor on 2011-06-16
This has happened a couple of times at seemingly completely random. The machine freezes and the fan increases up til maximum speed. 

I'm on Ubuntu 11.04 (now on 12.04) on a Toshiba Satellite R830-13D. 

One of the times I was in full screen mode in Dosbox, and figured it was a bug there. Another time I thought it was suspend. But today I had not used the machine for about an hour and the cord was in, so doubt it was suspend or hibernate.

I var/logs/ I've looked at syslog, kern.log, and auth.log.But the last entries were about 5 minutes before the crash.

Keyboard and mouse also freezes, so I can't go to alt-f1 etc out. Therefor it seems to be more than X, no?


Anything else I should look at? Any ideas as to what might cause this?

---

### Post by DirtyPC on 2011-06-16
It sounds more like hardware issue. 
I.e burnt out cpu, lack of RAM, fan issue.
Post your specs and the results of 'top' from the terminal. This will give us an indication to the amount of usage from your laptop. Thanks-

---

### Post by Quackers on 2011-06-16
Try booting with different boot options, such as noapic, nolapic or acpi=off and see if things improve.

---

### Post by Retor on 2011-06-19
Whao, you were fast. 

I also did good, and found [this thread where others have the same problem]("http://ubuntuforums.org/showthread.php?t=1760568&highlight=fan+r830"). Seems I'm not alone, so I'll try to upgrade the kernel first. 


Here's some info about the machine, anyhow. 
```

Prosessor:	Intel Core i5-2410M
Chipset:	Intel HM55 + ICH9M
Prosessor speed	2,3 GHz, 2,93GHz max turbo
Mem type	SODIMM DDR3 1333 MHz
Mem.	4GB
Harddisk size	640 GB
Harddisktype	SATA2 5400 rpm
Graphic card	Intel HD Graphics 3000
USB:	1 x 2.0, 1 x 3.0

```
Haven't tried the different boot options. It doesn't happen so often, just a pain when it does. 

Here's top:

```

top - 18:33:31 up 14 min,  2 users,  load average: 0.11, 0.17, 0.14
Tasks: 176 total,   2 running, 173 sleeping,   0 stopped,   1 zombie
Cpu(s):  4.3%us,  1.7%sy,  0.1%ni, 93.9%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   2741296k total,  1003852k used,  1737444k free,    56056k buffers
Swap:  4095996k total,        0k used,  4095996k free,   491796k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1617 rolf      20   0  100m  14m  10m S    7  0.5   0:02.00 unity-panel-ser    
 1429 rolf      20   0  209m  40m  20m S    5  1.5   0:21.12 compiz             
  951 root      20   0 65448  15m 8088 S    5  0.6   0:27.96 Xorg               
 2080 rolf      20   0  137m  22m  14m S    2  0.9   0:10.56 chromium-browse    
 1406 rolf      20   0  5208 2188  692 S    1  0.1   0:00.89 dbus-daemon        
 2099 rolf      25   5  158m  48m  18m S    1  1.8   0:09.17 chromium-browse    
 1683 rolf      20   0 34968  16m 9140 S    1  0.6   0:00.32 applet.py          
 1753 rolf      20   0  101m  22m  17m S    1  0.8   0:07.85 gnome-system-mo    
 2060 rolf      25   5  173m  53m  19m S    1  2.0   0:06.69 chromium-browse    
    3 root      20   0     0    0    0 S    0  0.0   0:00.04 ksoftirqd/0        
 1977 rolf      20   0  332m  63m  32m S    0  2.4   0:24.88 chromium-browse    
 2113 rolf      25   5  141m  27m  17m S    0  1.0   0:02.02 chromium-browse    
 2236 rolf      20   0 95820  14m  10m S    0  0.5   0:00.84 gnome-terminal     
    1 root      20   0  3016 1812 1248 S    0  0.1   0:00.81 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        

```

---

### Post by Retor on 2011-06-25
Didn't work. 

Now I think it's because I'm running 32 bit with 4 gb ram. 

uname -r gives: 2.6.39-0-generic
free -m results in:

```
             total       used       free     shared    buffers     cached
Mem:          2679       1001       1678          0         57        513
-/+ buffers/cache:        429       2249
Swap:         3999          0       3999

```

I'm trying to[ install PAE now]("http://www.cyberciti.biz/faq/ubuntu-linux-4gb-ram-limitation-solution/").

I also ran the memory test in windows 7, and that worked fine.But when I try the Memtest option at grub, it seems to freeze and fan goes nuts. 

So I hope PAE fixes it, or else I'll have to try 64

---

### Post by Retor on 2011-06-25
Downloaded memtest86+ 4.20, which has support for sandy bridge, and it ran. My memory is OK. 

After installing the PAE stuff, i now get: 

```
             total       used       free     shared    buffers     cached
Mem:          3926        969       2957          0         56        420
-/+ buffers/cache:        491       3434
Swap:         3999          0       3999

```

So lets hope fixed it. If it doesn't, I'll be back.

(Hope it's not a Sandy Bridge issue.)

---

### Post by tgalati4 on 2011-06-25
Install htop and keep it running.  Might be a runaway process.

sudo apt-get install htop
htop

---

### Post by Retor on 2011-07-05
@tgalati4: It doesn't happen that often, and when the system crashes, I can't switch to htop to see what process it might be. 

Anyhow. It froze again. So PAE gave me more memory, but it didn't solve the problem. 

None of the logs show any activity at the moment of the freeze. It froze at 11.34, and last log entry was at 11.17. 'twas about cron.

This time I was only running Firefox. Last time I was only running Chrome.

---

### Post by hawthornso23 on 2011-07-05
You mentioned it happening under low load so I wouldn't expect it to actually be hot enough to trigger a thermal shutdown. But a misconfigured thermal sensor that makes it THINK it is too hot might cause it to behave like this.

---

### Post by Retor on 2011-07-05
Just ran desktop recording while video transcoding just to use a lot of CPU to see if this was the problem, but the fan escalated nicely.

From acpi -V I'm now getting (while not using much CPU):

```
Battery 0: Discharging, 59%, 03:40:20 remaining
Battery 0: design capacity 6051 mAh, last full capacity 5537 mAh = 91%
Adapter 0: off-line
Thermal 0: ok, 56.0 degrees C
Thermal 0: trip point 0 switches to mode critical at temperature 102.0 degrees C
Cooling 0: LCD 4 of 7
Cooling 1: Processor 0 of 10
Cooling 2: Processor 0 of 10
Cooling 3: Processor 0 of 10
Cooling 4: Processor 0 of 10

```

---

### Post by hawthornso23 on 2011-07-05
Well that all looks normal enough.

---

### Post by Retor on 2011-07-08
It froze again. As the previous time, the last ting to occur was cron. But cron has also run between last time and this without any issues. 

This issue really puzzles me.  

kern
```
Jul  8 21:17:01 Toshen CRON[7662]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```
Sys
```
Jul  8 21:17:01 Toshen CRON[7662]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
```

auth
```
Jul  8 21:17:01 Toshen CRON[7660]: pam_unix(cron:session): session opened for user root by (uid=0)
Jul  8 21:17:01 Toshen CRON[7660]: pam_unix(cron:session): session closed for user root
```

Hum.. not sure what else to try. Perhaps another distro to see if it's ubuntu or linux in general.

---

### Post by Retor on 2011-07-08
> **Retor said:**
> 
kern
```
Jul  8 21:17:01 Toshen CRON[7662]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)

```
The /etc/cron.hourly folder is the only cron folder without a 0anacron script file. Seemes odd if that should cause the crash, though.

---

### Post by Retor on 2011-07-13
Tried Ubuntu Classic instead of Unity just to give it a shot. Still freezes and wheezes.

---

### Post by Retor on 2012-05-08
At some point an upgrade fixed this issue - allthough the batteries took a hit. Now the problem is back. 

I think it has something to do with Intel drives and sandy bridge boards.

---

