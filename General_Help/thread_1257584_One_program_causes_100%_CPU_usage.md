---
title: "One program causes 100% CPU usage"
date: 2009-09-04
forum: General Help
---

### Post by jukingeo on 2009-09-04
Hello all,

I am having trouble with a video editing program I am trying to learn called OpenShot. 

At first when I loaded the program on my system, it wouldn't run, it would just lock up the system and I would have to "Force Quit".  I was told to check my system resources by using the "top" command in my terminal.   Sure enough when I activated OpenShot it used the most resources...however, Firefox (which I usually have open) also used a good deal of resources.  Closing that out and ONLY running OpenShot allowed the program to run, however, the program is running very high on the resources (65% to 85%). That is cutting it close.

Anyway, I tried to export one of my finished pieces of work and once again the program gave me trouble, this time the program just kicked me out right to the desktop.  Once again I tried the "top" command and it was sitting right on 100% when I executed the export function.

Now this has me perplexed.  I am NOT running anything extra on my system, so I am figuring that some adjustments have to be made in order to optimize the CPU usage.

I don't consider my machine slow, but it sure isn't the fastest machine out there, but up until recently (with this program) I have not had many problems...this is the first time I am having one with CPU usage.

At any rate this is my system info:

Dell Dimension 4600
Intel P4 2.8ghz processor
2gig Ram
2 Seagate Sata 500gig hard drives
ATI Radeon 9600XT video card with 256meg ram
OS, multi boot with Ubuntu 8.04 (Hardy)
Program causing 100% usage: OpenShot
M-Audio Delta 44 audio card (Linux compatible)

When running the System Monitor, memory usage seems to be good and there is plenty of ram and plenty of space on the swap file.  It is just that I need to get this one program running as I want to use it for video editing.  I do not know what is causing the problem.

Here is my terminal using the 'top' command.  I have to show the usage of Firefox because I am composing this message while running the terminal:

 
Swap:  4305380k total,        0k used,  4305380k free,   467824k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 5456 root      20   0  556m  20m 8180 S  3.0  1.0   7:14.60 Xorg               
32400 geo       20   0  195m  61m  24m S  1.7  3.1   1:47.25 firefox            
 6037 geo       20   0 41164  22m  13m S  1.0  1.1   0:14.45 gnome-panel        
   15 root      10 -10     0    0    0 S  0.3  0.0   0:00.47 desched/0          
  933 geo       20   0  2308 1128  852 R  0.3  0.1   0:00.01 top                
 5924 geo       20   0 53772  22m 8748 S  0.3  1.1   0:02.54 gnome-settings-    
 6031 geo       20   0 21916  12m 7792 S  0.3  0.6   0:11.13 metacity           
 6038 geo       20   0 86608  40m  15m S  0.3  2.0   0:29.09 nautilus           
32361 geo       20   0 77028  19m  10m S  0.3  1.0   0:00.62 gnome-terminal     
    1 root      20   0  2844 1688  544 S  0.0  0.1   0:01.30 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 posix_cpu_timer    
    5 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 sirq-high/0        
    6 root     -51  -5     0    0    0 S  0.0  0.0   0:22.14 sirq-timer/0       
    7 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 sirq-net-tx/0      
    8 root     -51  -5     0    0    0 S  0.0  0.0   0:05.15 sirq-net-rx/0      
geo@home:~$ 


Firefox is only using 1.7 (but it does spike higher).

Now this is my "top" command using the OpenShot video editor. OpenShot is a Python based program:

wap:  4305380k total,        0k used,  4305380k free,   469264k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 3806 geo       20   0  138m  52m  16m S 47.2  2.6   0:05.67 python             
 5456 root      20   0  557m  22m 9588 S  8.6  1.1   7:19.35 Xorg               
 6030 geo       20   0 16388 2704 1744 S  1.0  0.1   0:22.70 gnome-screensav    
 6031 geo       20   0 21916  12m 7792 S  1.0  0.6   0:11.40 metacity           
 6037 geo       20   0 41164  22m  13m S  1.0  1.1   0:14.88 gnome-panel        
    6 root     -51  -5     0    0    0 S  0.3  0.0   0:22.46 sirq-timer/0       
   16 root      -2  -5     0    0    0 S  0.3  0.0   0:00.41 events/0           
 3150 root     -51  -5     0    0    0 S  0.3  0.0   0:06.45 IRQ-22             
 5924 geo       20   0 53772  22m 8748 S  0.3  1.1   0:02.58 gnome-settings-    
 7416 geo       20   0 26016  12m 7200 S  0.3  0.6   0:01.12 notification-da    
32361 geo       20   0 77424  20m  11m S  0.3  1.0   0:01.24 gnome-terminal     
    1 root      20   0  2844 1688  544 S  0.0  0.1   0:01.30 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 posix_cpu_timer    
    5 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 sirq-high/0        
    7 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 sirq-net-tx/0      
geo@home:~$ 

You see that?  It went to 47.2 CPU usage. Now I am going to run the export command:

Swap:  4305380k total,    91892k used,  4213488k free,   102944k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 7509 geo       20   0  142m  56m  15m S 93.4  2.8   0:49.78 python             
 5456 root      20   0  556m  20m 7044 S  1.0  1.0   7:24.39 Xorg               
 6038 geo       20   0 86608  38m  13m S  1.0  1.9   0:29.61 nautilus           
 6037 geo       20   0 41164  21m  12m S  0.7  1.1   0:16.08 gnome-panel        
    6 root     -51  -5     0    0    0 S  0.3  0.0   0:23.06 sirq-timer/0       
  793 root     -51  -5     0    0    0 S  0.3  0.0   0:00.24 IRQ-1              
 5065 root      20   0  4064 1144  916 S  0.3  0.1   0:09.54 atieventsd         
 6105 geo       20   0  2308 1140  856 R  0.3  0.1   0:00.35 top                
32361 geo       20   0 77748  20m  11m S  0.3  1.0   0:01.82 gnome-terminal     
    1 root      20   0  2844 1652  508 S  0.0  0.1   0:01.30 init               
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0        
    4 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 posix_cpu_timer    
    5 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 sirq-high/0        
    7 root     -51  -5     0    0    0 S  0.0  0.0   0:00.00 sirq-net-tx/0      
    8 root     -51  -5     0    0    0 S  0.0  0.0   0:05.15 sirq-net-rx/0      
    9 root     -51  -5     0    0    0 S  0.0  0.0   0:02.81 sirq-block/0 

Boom!  There you have it 100% CPU usage.

Now I would like to know if there is a way to adjust this within Ubuntu so it makes proper use of the CPU.  As you can see the rest of the processes I am running are nil.  I find it hard to believe that this program could be sucking up THAT much power.  I use Windows XP on the same system (dual boot) and I have run FAR more memory/CPU intense programs on that OS.

Any help would be appreciated.

Thank You,

Geo

---

### Post by Bucky Ball on 2009-09-04
Looks interesting. Have you tried asking the same questions on the OpenShot site?

[http://www.openshotvideo.com/2008/04/support.html](http://www.openshotvideo.com/2008/04/support.html)

I personally capture in Kino and edit in Cinelerra. I must admit though I usually capture in Kino and edit in Premiere Pro! I haven't found anything that comes close (yet).

---

### Post by jukingeo on 2009-09-04
> **Bucky Ball said:**
> Looks interesting. Have you tried asking the same questions on the OpenShot site?

[http://www.openshotvideo.com/2008/04/support.html](http://www.openshotvideo.com/2008/04/support.html)

Yes, I am in touch with the creator of OpenShot. We both agreed that I should look outside of OpenShot for issues (meaning issues with Ubuntu) and he is looking into issues with his program. Hopefully that way a solution can be found.

> 
I personally capture in Kino and edit in Cinelerra. I must admit though I usually capture in Kino and edit in Premiere Pro! I haven't found anything that comes close (yet).

Just about all the programs I have tried didn't work properly on my system, including Kino.  Cinelerra was the only one that ran without any trouble.  However, the learning curve is pretty steep and I wanted a program in which I can put videos together really fast but with audio editing capabilities (of which Windows Movie Maker lacks).  OpenShot looks like it will fit the bill.

If I DON'T run anything except OpenShot, I can create a work session and save it, the problem rears it's ugly head when I try to convert my edited material to a finished video file, then the CPU usage jumps to 100% and usually results in a crash or complete program shut down.

Geo

---

### Post by Bucky Ball on 2009-09-04
Check where your temp files are saving to when you do the conversion and where your converted file is landing. Best to have programs on one drive, capture and edit on another. 

If your temp files are landing in your Ubuntu install on that drive during the conversion that might be sending your CPU usage up. Just a wild stab. ... :)

---

### Post by jukingeo on 2009-09-10
> **Bucky Ball said:**
> Check where your temp files are saving to when you do the conversion and where your converted file is landing. Best to have programs on one drive, capture and edit on another. 

If your temp files are landing in your Ubuntu install on that drive during the conversion that might be sending your CPU usage up. Just a wild stab. ... :)

I have tried the program again, but with either the XFCE or LXDE interface.  CPU usage was still up there, but the lower resources of those gui interfaces was just enough to allow the program to fully run. I am going to do some more playing around in those interfaces to see which one I like better.  I been looking into a "lighter weight" version of Uubuntu anyway to set up dedicated use machines with.

Geo

---

### Post by Bucky Ball on 2009-09-10
In Xubuntu check:

System->Admin->Settings and hit keyboard. 

Make a new shorcut: command: firefox and choose which ever keys you want. Never have to touch the mouse again! Well, not quite but ... Have fun ...

---

### Post by gordintoronto on 2009-09-11
> **jukingeo said:**
>  CPU usage was still up there, but the lower resources of those gui interfaces was just enough to allow the program to fully run. 
Geo

A program which uses the CPU completely, still "fully runs."

When you export a video, the program might be "rendering" the images, which is very CPU intensive.  If you change the audio, that has to be embedded into the bytestream, which will take some serious CPU.

A friend of mine lives and breathes video creation, and he says there is no such thing as a CPU which is fast enough.

---

### Post by jukingeo on 2009-09-12
> **gordintoronto said:**
> A program which uses the CPU completely, still "fully runs."

Not always the case.  The video program I have shuts down.  However, I have found that when I use XFCE or LXDE interface, it WILL work.  But resources are just under 100%.   

> When you export a video, the program might be "rendering" the images, which is very CPU intensive.  If you change the audio, that has to be embedded into the bytestream, which will take some serious CPU.

A friend of mine lives and breathes video creation, and he says there is no such thing as a CPU which is fast enough.

LOL!  I guess that can be true.  Initially when you buy a computer the CPU is usually fast enough, but through time it does become obsolete and you need a bigger and faster CPU.

I have quite a few 'obsolete' machines and one of the big draws to Linux is that the OS makes good use of old equipment.  With some of the "lighter weight" distributions such as Xubuntu, Lubuntu, and Puppy Linux, you can squeeze out some good performance out of a machine that would barely run Windows XP.

Geo

---

