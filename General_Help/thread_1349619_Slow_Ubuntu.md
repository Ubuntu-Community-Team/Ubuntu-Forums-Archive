---
title: "Slow Ubuntu"
date: 2009-12-08
forum: General Help
---

### Post by superstalker on 2009-12-08
I got a problem, Ubuntu is getting slower and slower.

For example: 
- Starting up Ubuntu take over 3 minutes. I get a couple messages during that something hasn't been found or something, but it goes to fast to write down.
- When I'm multitasking, opening FF on one desktop, checking my mail on the other, etc. And I'm typing something it takes a few seconds when I'm done and Ubuntu also.

Now, as naive as I was, I thought, lets defragment it! But that is something Windows designed because there OS are THAT screwed up.


I'm still in the stage of experimenting with Ubuntu, so I'm thinking I've installed or screwed it up somehow, so it's getting slower. But I haven't got a clue what it is, or how to make a summary of errors...

Question: 
1. How can I fix it?
2. Is there a program that keeps track of what I'm doing to the system and that can guide me to fixing it (or where I can click on and it runs, fixing everything in a few minutes, while I'm getting a fresh cup of coffee, scratch my balls and everything works perfectly :D)
3. I really like messing with Ubuntu, like many others do, as fun as it is, inevitably the system will crash. Is there a sort of "live CD" that just checks and reinstalls the system back to default, instead of having to back up all the data, format your drive, install and restoring your data. (the reason why I ask, is that I'm guessing it'll be less then 7 days before in inevitable will happen)
EDIT: Or better yet, a bullet proof, uncrushable, fully experimental [ Ubuntu - OMGWTFFTW ] version ? 


Kind regards,
SuperStalker
[ Ubuntu 9.10 - the Karmic Koala ]                ( Fujitsu Siemens - Amilo Xi 2528 )
{ Intel Core 2 Duo T8100 - 2100 MHz - 3072 MB Internal Memory - NVIDIA GeForce 8600M GS }

---

### Post by LeifAndersen on 2009-12-08
First, assuming that your computer isn't literally dying (at which case the only thing you can do is get/make a new one), the first thing we need to do is determin what is taking up most of the CPU and RAM.  So, go to System -> Administration -> System Monitor.  Once their, go to the procese tab, and sort by both CPU and RAM.

Try to see what those processes are, and if you can shut them down.

Good luck.

---

### Post by superstalker on 2009-12-08
CPU:[ATTACH]139169[/ATTACH]
gnome-system-monitor 8% - 11%
firefox 1% - 3%

[ATTACH]139171[/ATTACH]
CPU 1: 14% - 25%
CPU 2: 16% - 30%
Screenlet CPU0: 20% - 40%

RAM: [ATTACH]139170[/ATTACH]
firefox 73,6 MiB
soffice.bin 48,4 MiB
evolution 15,6 MiB

RAM total: 2,5 GiB (86,5%)


Edit: 
This is weird, just was multitasking again, but system monitor hasn't recorded the CPU correctly... 
Recource CPU is around the 50% - 80%
Processes CPU is around 24%
Same goes for RAM... :S

---

### Post by superstalker on 2009-12-09
I've reviewed the system monitor and as long as everything is loaded everything is just fine. Except when I'm multitasking, then all of the sudden CPU is using 100% but the processes who use it, aren't displayed in the processes tab.

But I think we've started out wrong, 1stly, I want to speed up (re)starting the pc, as it's taking way to long IMO. For over 3 minutes.

---

### Post by pedro1hayling on 2009-12-09
Not sure EXACTLY what the prob is - I assume your running it from your HDD and NOT a CD ?
If the machine your running it on is your ONE AND ONLY computer I'd advise NOT to mess with it and accept the defaults offered else the inevitable WILL happen - and you will crawl away cursing Linux - and result in disappointment (as many others have) most systems will run quite happily as is after a new install - I have used  many variants of linux  and most modern distros are fine right out of the box - only tweaking for appearance or perhaps individual software packages.
The spec of your machine suggests that it should breeze along nicely - I'm running it on a 5 year old machine with only 1Gb of mem and it's still quicker than Windows - and renders better on screen with the same hardware.

Try a re-install - It might pay to have a go at another version of Linux as well.
Rgds:

---

### Post by superstalker on 2009-12-09
A re-install is something I'm trying to avoid.

Is there software available that can restore my system to default, so I don't have to re-install?
Or is there a way that I can post something from the terminal so you guys can see if I've installed something that slows this whole process down? I'm guessing it has to be related to the start-up errors.

It's kinda ridiculous that this (low) standard software is using 2.5 GiB...

---

### Post by gradinaruvasile on 2009-12-09
Best is top in a terminal.
Open a terminal, type

top

You will have your processes ordered by CPU usage by default (%CPU). 
Press shift+o, release, then q. This way you will have the processes ordered by memory usage (RES).
Press shift+o, release, then k. This way you will have the processes ordered by CPU again if you wish to switch back.

---

### Post by superstalker on 2009-12-09
CPU
  
PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND             
 17467 user    20   0 2390m 1.7g 171m S    4 56.6  34:19.04 VirtualBox          
 10721 user    20   0  693m 135m  19m S    2  4.5   6:05.47 firefox             
  1353 root      20   0  498m 120m  10m R    9  4.0  40:31.71 Xorg                
 14346 user    20   0  948m  66m  14m S    5  2.2  15:27.16 rhythmbox           
  2601 user    20   0  489m  45m  13m S    0  1.5   1:49.80 cairo-dock          
  2166 user    20   0  389m  45m  16m S   20  1.5  57:36.15 compiz.real         
  2171 user    20   0  457m  41m  10m S    0  1.4   0:45.87 gnome-panel         
 14745 user    20   0  324m  34m  11m S    5  1.1   0:01.59 gnome-terminal      
  2584 user    20   0  660m  23m  10m S    0  0.8   0:48.12 nautilus            
 17414 user    20   0  437m  22m  12m S    1  0.7   0:04.51 VirtualBox          
  2610 user    20   0  287m  21m 9100 S    0  0.7   0:04.48 python              
 11037 user    20   0  731m  21m  11m S    0  0.7   0:03.86 evolution           
  2591 user    20   0  269m  20m 8560 S    0  0.7   2:07.69 python              
  2593 user    20   0  369m  19m   9m S    1  0.6   2:05.93 python              
  2608 user    20   0  452m  17m  10m S    0  0.6   0:03.85 nm-applet           
 28905 user    20   0  170m  16m  11m R    2  0.6  15:22.27 npviewer.bin        
  2588 user    20   0  267m  16m 8572 S    3  0.5  10:18.24 python 



RAM

      	 	 	 	 	 	   RES USER     S %CPU  NI   PID  SHR  PR  VIRT %MEM    TIME+  COMMAND    
 1.7g user   S    1   0 17467 171m  20 2390m 56.6  34:24.31 VirtualBox 
 132m user   S    5   0 10721  20m  20  701m  4.4   6:21.56 firefox    
 120m root     R    8   0  1353  11m  20  499m  4.0  41:00.74 Xorg       
  89m user   S    1   0 15431  59m  20  680m  3.0   0:04.42 soffice.bin            
  66m user   S    5   0 14346  14m  20  946m  2.2  15:54.90 rhythmbox  
  45m user   S    1   0  2601  13m  20  489m  1.5   1:52.22 cairo-dock 
  45m user   S   19   0  2166  16m  20  389m  1.5  58:35.26 compiz.real            
  41m user   S    0   0  2171   9m  20  457m  1.4   0:46.50 gnome-panel            
  34m user   S    3   0 14745  11m  20  325m  1.2   0:03.48 gnome-terminal         
  23m user   S    0   0  2584  10m  20  660m  0.8   0:48.89 nautilus   
  22m user   S    0   0 17414  12m  20  437m  0.7   0:04.65 VirtualBox 
  21m user   S    0   0  2610 9120  20  287m  0.7   0:04.55 python     
  21m user   S    0   0 11037  11m  20  731m  0.7   0:03.95 evolution  
  20m user   S    1   0  2591 8576  20  269m  0.7   2:09.88 python     
  19m user   S    0   0  2593   9m  20  369m  0.6   2:08.08 python     
  17m user   S    0   0  2608  10m  20  452m  0.6   0:03.89 nm-applet  
  16m user   S    1   0  2588 8588  20  267m  0.5  10:29.25 python

---

### Post by superstalker on 2010-01-08
Found the error,

I installed so many thing that at a certain point the whole thing slowed down. Reinstalled ubuntu, installed only the packages I needed now it runs like old times again.

---

