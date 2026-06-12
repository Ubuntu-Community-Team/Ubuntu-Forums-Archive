---
title: "Really really really slow...."
date: 2010-10-27
forum: General Help
---

### Post by Adrienk on 2010-10-27
**Note: I do NOT want to have to reformat so only state that AS a LAST resort.**

I am running ubuntu 10.10 in a virtual box in windows 7 with 1 gig of ram, windows 7 is running 4 gigs.
I have noticed that ubuntu 10.10 is SOOOOOOOOOOOO SLOW, as in scrolling in eclipse takes a minute.

is there any way BESIDES reformatting that I can fix this? IF I must reformat how do I do this with OUT deleting or touching the I think it is home folder for my user, so basically reformat with OUT deleting my home folder and currently installed programs?

---

### Post by mikewhatever on 2010-10-27
I don't think reformatting would help, unless you know what the problem is and can avoid it after reformatting. Try looking at the amount of free disk space, RAM usage, CPU using processes.

---

### Post by sikander3786 on 2010-10-27
Did you install the Guest Additions? They really improve performance.

[http://www.virtualbox.org/manual/ch04.html](http://www.virtualbox.org/manual/ch04.html)

---

### Post by Adrienk on 2010-10-27
I did before the new update came out, I will re-install them and see if that helps. Because when it comes to the addons, there was some command line i had to enter, but I will re-install because VB when it came out with an update came out with new guest addons for ubuntu (linux in general) right?

---

### Post by Adrienk on 2010-10-27
I am finding that even after installing the addons its still slow.....

---

### Post by sikander3786 on 2010-10-27
> **Adrienk said:**
> I am finding that even after installing the addons its still slow.....
In that case are you sure you are not running out of diskspace as mikewhatever suggested above? Might also be some processes eating up the cpu/ram.

Take a look at your space usage by,

```
df -h
```

And take a look at active cpu/ram usage and processes by running

[/code]top[/code]

---

### Post by Adrienk on 2010-10-27
On a 16 gig hard drive which is set at dynamic expansion

running **df - h **I get

```
/dev/sda1              15G  5.6G  7.9G  42% /
none                  496M  236K  496M   1% /dev
none                  501M  368K  501M   1% /dev/shm
none                  501M  100K  501M   1% /var/run
none                  501M     0  501M   0% /var/lock
/dev/sr0               32M   32M     0 100% /media/VBOXADDITIONS_3.2.10_66523

```

And running **top** my biggest thing eating the cpu is:

adam (me the user) ant 25% 

I also have adam eclipse and firefox bin running both at about 19%

I have 1024mb's of ram and I have 22-28 mbs free (like wtf all I am running is the user adam, firefox and eclipse)

root sometimes uses 24% of my mem, BUT the only way im logged into root is by the terminal....

adding more ram does NOT fix the problem....

HELP?!

---

### Post by sikander3786 on 2010-10-27
So the problems is being caused by RAM alone I believe for now.

Can you please post the output of **top** while actively running all your needed applications.

```
top
```

and also this one

```
free
```

---

### Post by Adrienk on 2010-10-27
**top**

```
adam@adam-laptop:~$ top

top - 15:38:16 up  1:23,  2 users,  load average: 1.75, 1.71, 1.80
Tasks: 142 total,   2 running, 140 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.5%us, 62.9%sy,  0.0%ni, 31.9%id,  0.0%wa,  0.0%hi,  0.6%si,  0.0%st
Mem:   1025712k total,   944328k used,    81384k free,    97256k buffers
Swap:   704508k total,        0k used,   704508k free,   379656k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 2424 adam      20   0  245m  61m  26m S 20.2  6.1   5:21.82 firefox-bin        
  765 root      20   0  239m  62m  17m R 19.6  6.2  10:11.22 Xorg               
 1382 adam      20   0  221m  38m  12m S 11.9  3.8   5:24.96 compiz             
 2535 adam      20   0 90940  13m  10m S 10.3  1.3   0:04.41 gnome-terminal     
 1688 adam      20   0  990m 221m  37m S  4.5 22.1   7:40.32 eclipse            
 1581 adam      20   0 35056  18m 3984 S  1.9  1.9   1:13.76 ubuntuone-syncd    
 2558 adam      20   0  2624 1132  840 R  1.3  0.1   0:00.46 top                
 1427 adam      20   0  129m  18m  13m S  0.6  1.9   0:46.11 cairo-dock         
  877 mysql     20   0  151m  17m 5356 S  0.3  1.7   0:13.69 mysqld             
 1306 adam      20   0 98.3m  11m 8748 S  0.3  1.1   0:15.71 gnome-settings-    
 1428 adam      20   0 22192 9844 7404 S  0.3  1.0   0:31.00 emerald            
 1503 root      20   0  5616  724  452 S  0.3  0.1   0:03.23 udisks-daemon      
 1507 adam      20   0 19140 2244 1868 S  0.3  0.2   0:05.21 gvfs-afc-volume    
 1607 adam      20   0 72396  10m 8732 S  0.3  1.1   0:03.66 update-notifier    
    1 root      20   0  2876 1704 1220 S  0.0  0.2   0:03.46 init               
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.08 kthreadd           
    3 root      20   0     0    0    0 S  0.0  0.0   0:02.27 ksoftirqd/0        

```

**free:**

```

adam@adam-laptop:~$ free
             total       used       free     shared    buffers     cached
Mem:       1025712     945312      80400          0      97284     379656
-/+ buffers/cache:     468372     557340
Swap:       704508          0     704508


```

---

### Post by sikander3786 on 2010-10-27
Eclipse seems to eat most of the memory. Does Ubuntu work fine when you're not using Eclipse?

You've enabled compiz? Turning it off might improve performance.

---

### Post by Adrienk on 2010-10-27
With out any themes, compiz, emerald, eclipse, firefox or any other thing that eats up my memory....the system is still slow and sluggish but the start up and shut down ar still speedy....

---

### Post by 4Orbs on 2010-10-27
Completely out of my element here, but I'll make a wild guess. Eclipse, being a java development tool, would probably run better if you were to replace the open java environment with the sun java environment.

---

### Post by Adrienk on 2010-10-27
I just installed the eclipse via the terminal so I am not sure if it is using the open or the non open java envrio

But my vm became sluggish after I upgraded......

Why?

---

