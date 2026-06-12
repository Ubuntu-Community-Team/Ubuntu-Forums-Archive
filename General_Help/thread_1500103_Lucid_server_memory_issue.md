---
title: "Lucid server memory issue"
date: 2010-06-02
forum: General Help
---

### Post by aboud on 2010-06-02
Hey there .. 

I used to use server 64, and it handled memory well with Jaunty and Karmic but with Lucid the memory usage is always high and can't run virtual machines. 
```

00:38 :~>free -m 
             total       used       free     shared    buffers     cached
Mem:          1999       1969         29          0         69        431
-/+ buffers/cache:       1468        530
Swap:         1906          0       1906

```

I am not using any extra app other than I used to use . 

any one has clue to what is going on ?

---

### Post by cariboo on 2010-06-02
Run top from the prompt to see what is using all your resources.

---

### Post by dcstar on 2010-06-03
> **aboud said:**
> Hey there .. 

I used to use server 64, and it handled memory well with Jaunty and Karmic but with Lucid the memory usage is always high and can't run virtual machines. 
```

00:38 :~>free -m 
             total       used       free     shared    buffers     cached
Mem:          1999       1969         29          0         69        431
-/+ buffers/cache:       **1468 **       530
Swap:         1906          0       1906

```

I am not using any extra app other than I used to use . 

any one has clue to what is going on ?

Cached files are using most of the memory and will be replaced with apps when required, so what is the actual problem?

---

### Post by rnerwein on 2010-06-03
hi
aboud's problem is not the cache: used ( 1969 ) - buffers ( 69 ) - cached ( 431 ) = real used memoy ( 1468 ).
this is the used memory without cache.
i guess - is there shared memory involed  ( ipcs -m ) ?
or just processes with huge rss-memory.
ciao

---

### Post by aboud on 2010-06-03
here is the head 10 line of top sorted by memory  
```

[SIZE="1"]USER       PID %CPU 	  %MEM    VSZ   RSS TTY      STAT START   TIME COMMAND
aboud     2752  4.5 	  5.1 328088 105108 ?       S    00:23  36:21 compiz
root      2622  3.1 	  2.1 135800 44668 tty8     Ss+  00:22  24:44 /usr/bin/X :0 -br -verbose -auth /var/run/gdm/auth-for-gdm-DpXS7r/database -nolisten tcp
aboud     2766  0.0 	  1.9 541128 40304 ?        S    00:23   0:08 nautilus
aboud     2764  0.0 	  1.2 267548 26324 ?        S    00:23   0:03 gnome-panel
aboud     5511  0.0 	  1.1 341608 23900 ?        S    08:05   0:01 /usr/lib/gnome-panel/clock-applet --oaf-activate-iid=OAFIID:GNOME_ClockApplet_Factory --oaf-ior-fd=25
root      6292  0.1 	  0.9  47792 20324 pts/0    S+   13:26   0:00 apt-get install wine
aboud     2826  0.0 	  0.7 430432 14404 ?        Sl   00:23   0:00 /usr/lib/evolution/2.28/evolution-alarm-notify
aboud     2747  0.0 	  0.7 323608 14528 ?        Ss   00:23   0:02 /usr/lib/gnome-settings-daemon/gnome-settings-daemon[/SIZE]
```

as for ipsc -m  I don't understand much of it
```

------ Shared Memory Segments --------
key        shmid      owner      perms      bytes      nattch     status      
0x00000000 1638400    root       777        135168     2                       
0x00000000 1769473    aboud      600        393216     2          dest         
0x00000000 1802242    aboud      600        393216     2          dest         
0x00000000 1835011    aboud      600        393216     2          dest         
0x00000000 1867780    aboud      600        393216     2          dest         
0x00000000 1900549    aboud      600        393216     2          dest         
0x00000000 1933318    aboud      600        393216     2          dest         
0x00000000 1966087    aboud      600        393216     2          dest         
0x00000000 2654216    aboud      600        393216     2          dest         
0x00000000 2686985    aboud      600        393216     2          dest         
0x00000000 2588682    aboud      600        393216     2          dest         
0x00000000 2621451    aboud      600        393216     2          dest         
0x00000000 2719756    aboud      600        393216     2          dest         
0x00000000 2752525    aboud      600        12288      2          dest         
0x00000000 2785294    aboud      600        12288      2          dest         
0x00000000 3178511    aboud      600        393216     2          dest         
0x00000000 2981904    aboud      600        393216     2          dest         
0x00000000 3407889    aboud      600        393216     2          dest         
0x00000000 3440658    aboud      600        393216     2          dest   

```

---

### Post by rnerwein on 2010-06-03
hi
first of all: top ain't show to much memory usage.
second: your --> 
[SIZE=1]apt-get install wine is running more than 13 minutes. that looks strange for me. but i never used wine before.
third: it's not shared memory in your case - sorry
sorry i can't help any more.
ciao
oh shared memory means what the name say --> it's shared.
e.g. you got 100 tasks running and every task is attached to the same shared memory segment of, lets say 1GB, you see in top or ps aux VSZ.
if it is really the same the same segment the memory is used only once not 100 * 1 GB.
shared memory is mostely used by database aplications.
hope this helps a little.
ciao

[/SIZE]

---

### Post by bodhi.zazen on 2010-06-03
Not sure what is using all those resources, but may I ask why are you running a desktop + wine on a server ?

Close all X applications, disable all unnecessary services, etc. Ubutnu desktop includes a number of services you do not need on a server and these will use resources.

---

### Post by aboud on 2010-06-04
> **bodhi.zazen said:**
> Not sure what is using all those resources, but may I ask why are you running a desktop + wine on a server ?

Close all X applications, disable all unnecessary services, etc. Ubutnu desktop includes a number of services you do not need on a server and these will use resources.

thou I am not IT guru, there is no way I can convince every one else in the house of it. 

I put the server edition because it is server and desktop at the same time, it is the main pc all other computers connect to the Internet through it, play media from its hards,  that what i used to do I might be wrong 

after stopping gdm here is the top sort by memory ( file attached ) still used memory 1259.

main problem is I can't start virtual XP that I used to.

---

### Post by lavinog on 2010-06-07
Since you are running compiz, you should try running glxinfo and see if it frees up your memory.
There is a memory leak with some drivers.  For some strange reason running glxgears or glxinfo frees the lost memory.

What some users are doing is writing a script that runs glxinfo every couple of mins.
Disabling desktop effects can also fix this issue.

---

### Post by aboud on 2010-08-30
Thank you all for your help. 

I have added another 2G memory. Now every things is OK.

---

