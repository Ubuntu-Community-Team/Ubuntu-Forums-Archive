---
title: "Very high CPU activity w/ all processes sleeping"
date: 2010-09-18
forum: General Help
---

### Post by Ol'manScratch on 2010-09-18
Hello all

Ubuntu 10.4 Karmic on a Phenom quad core + 4 GB ram

Problem: CPU running all 4 cores at up to 80% and 20% memory, but all sys monitor shows processes sleeping except sys monitor.
I have looked at the logs, but I don't know enough about what I'm looking for.
I have Firefox up, but I'm not browsing and it is slowing my system. I can live with the slow down as it's not too bad. I am concerned about the CPU activity.
Monitor shows a fairly static memory use at 19.5% of available ram and memory and swap file is flatlined despite the memory use.
Network activity shows flat - then spikes - and returns to flat.

What is the problem and how do I fix it. I someone will tel which part of the log file to post, I will

Thanks

Network activity

---

### Post by MooPi on 2010-09-18
No that level of activity is unacceptable. Does this persist after a reboot ? If your using firefox are you viewing flash video ?

---

### Post by Ol'manScratch on 2010-09-18
I didn't think of rebooting I will now. If a reboot doesn't work are other ways to determine the problem?
Thanks

---

### Post by cj.surrusco on 2010-09-18
Maybe it could be a zombie process? I think that would show up in the System Monitor, though. Definitely try rebooting first.

---

### Post by mr clark25 on 2010-09-18
if the problem persists after you restart, open a terminal and run:
```

top

```

copy/paste the output here so we can look at it and tell what is eating your cpu.

---

### Post by The Cog on 2010-09-18
System monitor defaults to only showing your own processes. Check under the View menu. I prefer the command-line top (or better still htop but package htop isn't installed by default).

---

### Post by Ol'manScratch on 2010-09-18
Ok, I rebooted, but CPU2 and 4 were running 40 to 50 % while CPU 1 and 3 were at zero. Then then all of them began running high.
I'll see what top does. BRB

---

### Post by Ol'manScratch on 2010-09-18
here's what top shows. It also shows 2 users. I'm the only one using it. I do have another comp running of the same router. Does that make a difference?


jess@jess-desktop:~$ top

top - 16:06:41 up 21 min,  2 users,  load average: 0.00, 0.01, 0.00
Tasks: 179 total,   3 running, 176 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.0%us,  2.7%sy,  0.0%ni, 77.3%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   3800160k total,   816052k used,  2984108k free,    50572k buffers
Swap:  5261248k total,        0k used,  5261248k free,   229688k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1364 root      20   0  425m  37m 9.8m R   55  1.0   3:36.70 Xorg               
 1889 jess      20   0  226m  20m  14m S   39  0.6   2:20.98 gnome-system-mo    
 1905 jess      20   0  210m  14m   9m S    1  0.4   0:00.73 gnome-terminal     
 1837 jess      20   0  823m 193m  31m S    0  5.2   0:23.28 firefox-bin        
 1926 jess      20   0 19140 1384  992 R    0  0.0   0:00.32 top                
    1 root      20   0 19460 1808 1208 S    0  0.0   0:01.00 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.03 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/3        
jess@jess-desktop:~$ top

top - 16:07:16 up 22 min,  2 users,  load average: 0.00, 0.00, 0.00
Tasks: 179 total,   3 running, 176 sleeping,   0 stopped,   0 zombie
Cpu(s): 23.2%us,  1.5%sy,  0.0%ni, 74.9%id,  0.2%wa,  0.1%hi,  0.2%si,  0.0%st
Mem:   3800160k total,   814004k used,  2986156k free,    50588k buffers
Swap:  5261248k total,        0k used,  5261248k free,   229712k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1364 root      20   0  421m  37m 9.8m R   59  1.0   3:57.81 Xorg               
 1889 jess      20   0  226m  20m  14m S   41  0.6   2:34.49 gnome-system-mo    
 1869 jess      20   0  399m  26m  16m S    1  0.7   0:02.38 plugin-containe    
 1905 jess      20   0  210m  14m   9m S    1  0.4   0:00.82 gnome-terminal     
 1837 jess      20   0  823m 191m  31m S    0  5.2   0:24.08 firefox-bin        
 1930 jess      20   0 19140 1384  992 R    0  0.0   0:00.05 top                
    1 root      20   0 19460 1808 1208 S    0  0.0   0:01.00 init               
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.03 ksoftirqd/0        
    5 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT  -5     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/2        
   11 root      RT  -5     0    0    0 S    0  0.0   0:00.00 watchdog/2         
jess@jess-desktop:~$

---

### Post by cj.surrusco on 2010-09-18
Okay, it definitely seems like Xorg is the issue. I've never had it happen to me, but here is a solution that worked for someone else that I found on Google. 

[http://blog.kelsin.net/2009/02/24/slow-firefox-high-xorg-cpu-usage-debian-and-ubuntu-solved/](http://blog.kelsin.net/2009/02/24/slow-firefox-high-xorg-cpu-usage-debian-and-ubuntu-solved/)

---

### Post by Ol'manScratch on 2010-09-18
I don't see Xorg as a process in the sys monitor or the file browser. How do I access it? Sorry, I'm not as good with Ubu as I should be by now.

Thanks for your help.

---

### Post by Ol'manScratch on 2010-09-18
Here's an interest fact - the Xorg process shows as sleeping while the COU rate continues to flux from high to very high.

---

### Post by Ol'manScratch on 2010-09-18
Here's an interesting fact - the Xorg process shows as sleeping while the CPU rate continues to flux from high to very high.

---

### Post by mr clark25 on 2010-09-18
> **Ol'manScratch said:**
> I don't see Xorg as a process in the sys monitor or the file browser. How do I access it? Sorry, I'm not as good with Ubu as I should be by now.

Thanks for your help.

the command "top" is basically a system monitor in the terminal. i like it a lot better than "system monitor".


in that link, they talk about editing "xorg.conf". that is a text file. doing this is surprisingly easy.

run these two commands: (the first one makes a backup, and the second brings up a text editor)
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_orig
sudo gedit /etc/X11/xorg.conf

```go down to the very bottom of the text file, and paste this in it, on it's own line:

(was going to paste it here...)

EDIT:looks like it wont copy/paste here for some reason, go to the link that was given and copy/paste it from there.

also, you will need to logout and log back in for the changes to take affect.

---

### Post by Ol'manScratch on 2010-09-18
Ok, I am confused again. in that link, they talk about editing "xorg.conf". that is a text file.

Is this the link you want me to view: [http://blog.kelsin.net/2009/02/24/slow-firefox-high-xorg-cpu-usage-debian-and-ubuntu-solved/](http://blog.kelsin.net/2009/02/24/slow-firefox-high-xorg-cpu-usage-debian-and-ubuntu-solved/)

All I saw was a thread on slow firefox and  relating to the i810 driver 
"As I said in an above reply, this fix is for a bug in the i810 driver  (intel graphics cards you find in non-gaming laptop and computers  largely built into motherboards.) 

It also was very specific in what was slowed down. Not the whole  computer but drawing GTK apps specifically. Firefox switching tabs was  the largest slow down.
 
"As I said in an above reply, this fix is for a bug in the i810 driver  (intel graphics cards you find in non-gaming laptop and computers  largely built into motherboards.) "
 

 ... "Try it             at your own risk if you're on a Intel card with a weird, very-slow Firefox." Kelsen also said:

---

