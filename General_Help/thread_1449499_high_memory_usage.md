---
title: "high memory usage"
date: 2010-04-07
forum: General Help
---

### Post by DonutPower on 2010-04-07
just installed Ubuntu 9.10 on an old Dell Dimension 4400 PC. system has a 1.5GHz Pentium 4 Processor. 640MB of RAM.  a Radeon HD 2400 AGP video card. and a USB wi-fi adapter.

i installed and briefly used Ubuntu  back in 2005/2006 i believe, when having access to a computer lab in college. so im not completely new to it, but still dont know my way around it as far as customization  and maintenance goes. which is the intent of using it on this old PC, is to get more experience with it. i prefer Mac OS X but i wanted to try something different that isnt Windows. 

when trying to surf the net on Firefox or just opening an application it seemed too sluggish. i know this PC is old but it usually gives decent performance for just surfing the net or launching an app when in Windows XP, even Windows 7 was quite fair with performance on it. 

when i load up system monitor, even that feels sluggish. it shows that only a few MBs are in use by processes.all of them are shown as Sleeping. which not sure what that means, since even while im using Firefox and going from page to page it still shows Firefox as Sleeping. 
the top 3 shown are Xorg with 17MB,  jockey-backend with 15MB, and Nautilis with 10MB. the rest are all under 10MB majority taking up 1MB or so. adding all those up would still be under 100MB. yet the usage i see reported is usually over 500MB and CPU usage is always high. if im just using Ubuntu Software Center the cpu usage is always 100%. when the system is idle 54% or more is usually shown.

after a reboot and just leaving it alone, ive noticed that the memory starts at about 200MB which to me seems normal. but the number will slowly climb and within 15 minutes it shows 500MB or so in usage. and the number slowly climbs up as the seconds pass.   yet system monitor doesnt show what process is taking up all this.  i added system monitor to the panel so i could always see the graphs for memory and cpu. 

tried googling to see if there were any processes at startup or running in the background that i could disable to free up some memory. but when i go to System>Administration , i see no Services app listed like its shown in screenshots.  

so figured i would visit here and see if anyone could help me out or point me in the right direction.

---

### Post by Revolutionary101 on 2010-04-07
To see what processes might be taking up the memory, open up system monitor. Then click on view and select All processes. That should show whats hogging the memory.

---

### Post by linden940 on 2010-04-07
can you post this for us

```
free -mc
```

---

### Post by DonutPower on 2010-04-07
thats how i always view it.  it doesnt show me anything thats taking up more than 20MB. the highest it shows is 21.4MB from Xorg. 

if i use Firefox its usually at 46 to 51MB at most. yet the memory usage just keeps climbing little by little.

---

### Post by linden940 on 2010-04-07
how fast dos it go? are we talking by a few hrs or a few days?

---

### Post by DonutPower on 2010-04-07
a few minutes.

---

### Post by DonutPower on 2010-04-07
> **linden940 said:**
> can you post this for us

```
free -mc
```


you mean free -m   ??

---

### Post by linden940 on 2010-04-07
if you could post the ```
free -m
``` that would be helpful

and 640MB of ram is not alot to start with so when you have compiz and the other things as well..it will take of a good bit of ram....maybe xubuntu would be better for your system?

---

### Post by DonutPower on 2010-04-07
well 640 was enough for when using Windows XP and Win7. i dont use the PC a whole lot so i never saw the need to upgrade the RAM since it maxes at 1GB. compiz only shows as being like 600K or so. when i installed the OS, i had it set to basic instead of having the fancy effects which im sure would decrease system performance. 

heres what it shows me. i did it 3 times , once every couple of minutes. with no other apps running.
```
     

donut@donut-dell-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           623        509        113          0         25        148
-/+ buffers/cache:        335        287
Swap:          839          0        839

donut@donut-dell-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           623        614          8          0         19        165
-/+ buffers/cache:        430        192
Swap:          839          0        838

donut@donut-dell-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           623        613          9          0          7         92
-/+ buffers/cache:        513        109
Swap:          839         16        822
donut@donut-dell-desktop:~$ 






```

---

### Post by nismo_2005 on 2010-04-07
my old setup was only 512mb of ram and i had compiz running plus simple ccsm with max/min effects and i would idle at just over 190mb use. and that old p4 2.26ghz ran pretty snappy.


-edit- one other thing im a ubuntu noob myself. but what is your swappiness? one of the other more experienced people can step in but if it is set low wouldn't that cause high ram usage?

---

### Post by DonutPower on 2010-04-07
> **nismo_2005 said:**
> my old setup was only 512mb of ram and i had compiz running plus simple ccsm with max/min effects and i would idle at just over 190mb use. and that old p4 2.26ghz ran pretty snappy.


thats whats thrown me for a loop. i thought Ubuntu would run great on it, even when i got OS X installed on it, it ran as good as a Mac Mini.

---

### Post by linden940 on 2010-04-07
> **DonutPower said:**
> well 640 was enough for when using Windows XP and Win7. i dont use the PC a whole lot so i never saw the need to upgrade the RAM since it maxes at 1GB. compiz only shows as being like 600K or so. when i installed the OS, i had it set to basic instead of having the fancy effects which im sure would decrease system performance. 

heres what it shows me. i did it 3 times , once every couple of minutes. with no other apps running.
```
     

donut@donut-dell-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           623        509        113          0         25        148
-/+ buffers/cache:        335        287
Swap:          839          0        839

donut@donut-dell-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           623        614          8          0         19        165
-/+ buffers/cache:        430        192
Swap:          839          0        838

donut@donut-dell-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           623        613          9          0          7         92
-/+ buffers/cache:        513        109
Swap:          839         16        822
donut@donut-dell-desktop:~$ 






```


from what i see there dose seem to be a ram hog...maybe...cant remember that post someone listed to show a "ghost" program that was running that cant be seen....i knew i should of saved that one.

BUT i SHOULD be ok your swap is set at 839 an the most from the post that you have put there is 16...that means you got 822 of swap still usable.

so you got like 1462 of "ram" that your system can use only thing that pops out at me is this part

             total 

Mem:           623
Swap:          839

your swap should be smaller than the amount of ram chips u have IN your computer 839(Swap) - 623(Mem) = 216(Swap)

did you go and play around with any settings in your computer?

---

### Post by DonutPower on 2010-04-08
> **linden940 said:**
> from what i see there dose seem to be a ram hog...maybe...cant remember that post someone listed to show a "ghost" program that was running that cant be seen....i knew i should of saved that one.

BUT i SHOULD be ok your swap is set at 839 an the most from the post that you have put there is 16...that means you got 822 of swap still usable.

so you got like 1462 of "ram" that your system can use only thing that pops out at me is this part

             total 

Mem:           623
Swap:          839

your swap should be smaller than the amount of ram chips u have IN your computer 839(Swap) - 623(Mem) = 216(Swap)

did you go and play around with any settings in your computer?

nope thats the way it was when i installed it. the only thing i did was do the updates and then i installed VLC. i havent gotten around to doing much on it because it seems the internet keeps disconnecting at random moments. after the install, i couldnt get the net going until i put in the DNS servers.it shows my usb wi-fi adapter and connects to the network just fine, always has a strong signal showing even when i cant load a webpage. only way i can get the net back is if i disconnect from the network and then reconnect. but it still screws up at random.

---

### Post by linden940 on 2010-04-08
ok try this and post this

type top into terminal and then after it comes hit the key u then the name of your computer...it should list all things

---

### Post by linden940 on 2010-04-08
u should see something like this

```
top - 23:03:57 up 7 days,  6:53,  2 users,  load average: 0.02, 0.05, 0.02
Tasks: 157 total,   2 running, 155 sleeping,   0 stopped,   0 zombie
Cpu(s): 18.8%us,  2.3%sy,  0.0%ni, 78.1%id,  0.0%wa,  0.0%hi,  0.8%si,  0.0%st
Mem:   4059968k total,  2831680k used,  1228288k free,   212624k buffers
Swap:  9936160k total,        0k used,  9936160k free,  1843832k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
23339 ubuntu    20   0  216m  41m  15m R   17  1.0   3:35.58 npviewer.bin       
 1722 ubuntu    20   0  356m 104m  24m S    7  2.6  87:01.77 compiz.real        
21116 ubuntu    20   0  780m 174m  30m S    2  4.4  21:04.17 firefox            
23541 ubuntu    20   0  215m  15m  10m S    2  0.4   0:00.98 gnome-terminal     
 1613 ubuntu    20   0  265m 5400 3748 S    0  0.1   5:50.77 pulseaudio         
 1548 ubuntu    20   0 96796 3904 3020 S    0  0.1   0:00.01 gnome-keyring-d    
 1563 ubuntu    20   0  167m 8868 6652 S    0  0.2   0:00.60 gnome-session      
 1603 ubuntu    20   0 36060  704  272 S    0  0.0   0:00.67 ssh-agent          
 1606 ubuntu    20   0 24204 1804  648 S    0  0.0   0:03.54 dbus-daemon        
 1607 ubuntu    20   0 26156  768  472 S    0  0.0   0:00.00 dbus-launch        
 1616 ubuntu    20   0 94308 3432 2676 S    0  0.1   0:00.01 gconf-helper       
 1618 ubuntu    20   0 46344 6224 2324 S    0  0.2   0:27.00 gconfd-2           
 1626 ubuntu    20   0  192m 9364 6552 S    0  0.2   0:00.24 seahorse-daemon    
 1627 ubuntu    20   0  319m  14m 9.8m S    0  0.4   0:21.73 gnome-settings-    
 1632 ubuntu    20   0 43604 2784 1924 S    0  0.1   0:00.12 gvfsd              
 1637 ubuntu    20   0 75492 2800 2104 S    0  0.1   0:00.00 gvfs-fuse-daemo    
 1656 ubuntu    20   0  199m  14m 9428 S    0  0.4   0:07.62 notify-osd 
```

---

### Post by linden940 on 2010-04-08
maybe you have a zombie?

---

### Post by linden940 on 2010-04-08
post that and i'll check it in the morning...i have been up to late trying 2 help u as it is..i need to get up in a few hrs...post that an i'll look as soon as i can...that or maybe someone else can help you at this time

---

### Post by DonutPower on 2010-04-08
```
     

top - 23:15:03 up  1:00,  2 users,  load average: 0.51, 0.28, 0.21
Tasks: 133 total,   3 running, 130 sleeping,   0 stopped,   0 zombie
Cpu(s): 43.4%us,  7.3%sy,  0.0%ni, 48.7%id,  0.0%wa,  0.7%hi,  0.0%si,  0.0%st
Mem:    638088k total,   577624k used,    60464k free,     8552k buffers
Swap:   859436k total,    45936k used,   813500k free,   112580k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                             
 3828 donut     20   0 35936  14m  10m S 12.6  2.3   5:47.00 gnome-system-mo                     
 3780 donut     20   0 38436  12m 9232 R  6.0  2.0   0:04.98 gnome-terminal                      
 3622 donut     20   0 30964  17m 6424 S  2.7  2.8   0:34.13 compiz.real                         
 3624 donut     20   0 93152  21m  11m S  1.3  3.5   0:04.35 nautilus                            
 3664 donut     20   0 31564  10m 8068 S  0.3  1.7   0:05.81 multiload-apple                     
 4051 donut     20   0  2472 1172  884 R  0.3  0.2   0:00.46 top                                 
 3436 donut     20   0 40708 2316 2280 S  0.0  0.4   0:00.03 gnome-keyring-d                     
 3451 donut     20   0 25520 5624 5088 S  0.0  0.9   0:00.29 gnome-session                       
 3494 donut     20   0  4712  264  232 S  0.0  0.0   0:00.01 ssh-agent                           
 3498 donut     20   0  3384  440  436 S  0.0  0.1   0:00.00 dbus-launch                         
 3499 donut     20   0  3108 1288  628 S  0.0  0.2   0:00.57 dbus-daemon                         
 3503 donut     20   0 99.9m 1828 1484 S  0.0  0.3   0:00.49 pulseaudio                          
 3507 donut     20   0 10636 2084 2080 S  0.0  0.3   0:00.02 gconf-helper                        
 3509 donut     20   0  7592 3208 2040 S  0.0  0.5   0:01.96 gconfd-2                            
 3519 donut     20   0 96464 6412 5656 S  0.0  1.0   0:01.46 gnome-settings-                     
 3521 donut     20   0 22424 4840 4504 S  0.0  0.8   0:00.18 seahorse-daemon                     
 3526 donut     20   0  5748 1912 1728 S  0.0  0.3   0:00.05 gvfsd                               
 3532 donut     20   0 17460 5096 4884 S  0.0  0.8   0:00.14 notify-osd                          
 3533 donut     20   0 29796 2040 1900 S  0.0  0.3   0:00.01 gvfs-fuse-daemo                     
 3544 donut     20   0  1752  456  452 S  0.0  0.1   0:00.02 compiz                              
 3623 donut     20   0 42544  14m  10m S  0.0  2.3   0:10.51 gnome-panel                         
 3626 donut     20   0 40600 3048 2256 S  0.0  0.5   0:00.10 bonobo-activati                     
 3628 donut     20   0 19948 6548 5116 S  0.0  1.0   0:04.18 vino-server                         
 3629 donut     20   0 17152 6108 4856 S  0.0  1.0   0:00.15 gdu-notificatio                     
 3630 donut     20   0 34744  11m 7692 S  0.0  1.8   0:01.60 nm-applet                           
 3633 donut     20   0 16696 5244 4160 S  0.0  0.8   0:00.07 polkit-gnome-au                     
 3634 donut     20   0 27128  10m 7808 S  0.0  1.7   0:00.54 update-notifier                     
 3635 donut     20   0 94364 9.8m 7372 S  0.0  1.6   0:00.32 gnome-volume-co                     
 3639 donut     20   0 26232 9372 6788 S  0.0  1.5   0:00.49 gnome-power-man                     






```

---

### Post by linden940 on 2010-04-08
just saw that before i loged out..so doin a fast post

from what i see there..its all as it should other than that your swap is "over" sized  but there seems to be no ghost running

BUT you do have swap that can be used

other than what i have all ready done i cant help you any more than i have

---

### Post by DonutPower on 2010-04-08
so everythings normal? cause right now in System Monitor it shows 512is being used up.
swap is showing as using 48.2 out of the 839.  

while all i got running now is Firefox that system monitor shows only taking up 52MB having 3 tabs open.

thats what seems a bit excessive for only having 1 app going. 

what bothers me is just in having system monitor on the desktop and having it in the foreground or clicking through its tabs, it shows as 46% CPU usage. just with having it in focus. making everything else such as clicking anything in the menubar seem so sluggish or unresponsive.

---

### Post by linden940 on 2010-04-08
it looks fine from what i can tell..yes

---

### Post by nismo_2005 on 2010-04-08
well my system monitor says im using 191mb but tis is what free -m says.


> eddie@eddie-desktop:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          2011       1960         51          0         31       1336
-/+ buffers/cache:        592       1418
Swap:         3922          0       3922
eddie@eddie-desktop:~$ 



so i dont know what to think of it. and i got about the same results on a dell mini 10

---

### Post by DonutPower on 2010-04-08
> **linden940 said:**
> it looks fine from what i can tell..yes

i tinkered around with it a bit looking to see if i was just lacking an update or driver. when i disabled the video card driver, i noticed better performance and the RAM usage stayed low. but when surfing the net, images and text get all scrambled and distorted whenever i scroll a page. so i enabled the driver and now RAM seems to stay below 300MB but its only been on for about 20 minutes. 

so not sure whats going on there.

i just wanted to an OS that is lightweight but can still run Firefox (YouTube and Hulu vids)and play vids with VLC.

---

### Post by lavinog on 2010-04-08
Is this 32bit or 64bit?

On one of your posts you had npviewer.bin being at the top of the list.  npviewer.bin is part of adobe flash and has been known to have issues in 64bit systems.  If this is a 64bit system you can benefit by installing the 64bit alpha from adobe.

---

### Post by DonutPower on 2010-04-08
> **lavinog said:**
> Is this 32bit or 64bit?

On one of your posts you had npviewer.bin being at the top of the list.  npviewer.bin is part of adobe flash and has been known to have issues in 64bit systems.  If this is a 64bit system you can benefit by installing the 64bit alpha from adobe.

well that was the flash package that i found after reading some articles about Ubuntu.  my Dell is 32bit. got the thing in 2002. so its quite old.

---

### Post by lavinog on 2010-04-08
> **linden940 said:**
> 
your swap should be smaller than the amount of ram chips u have IN your computer 839(Swap) - 623(Mem) = 216(Swap)

did you go and play around with any settings in your computer?

Where did you get your information?
The traditional rule of thumb is that your swap should be 1.5x your ram.
Part of this is for hibernation reasons...you need to be able to fit all of your memory in swap when you hibernate.

If you have plenty of memory, you can ignore this rule, but in the op's case 640m is not considered plenty.

@OP: What type of memory does this system use? Is it rdram?

Would you consider upgrading to Lucid Beta2 and seeing if the memory issue still persists?

---

### Post by DonutPower on 2010-04-08
> **lavinog said:**
> Where did you get your information?
The traditional rule of thumb is that your swap should be 1.5x your ram.
Part of this is for hibernation reasons...you need to be able to fit all of your memory in swap when you hibernate.

If you have plenty of memory, you can ignore this rule, but in the op's case 640m is not considered plenty.

@OP: What type of memory does this system use? Is it rdram?

Would you consider upgrading to Lucid Beta2 and seeing if the memory issue still persists?

its got the stock Dell memory in it. which is DDR SDRAM  i think. its got the 128MB chip and in the second slot is a 512MB chip.

i wouldnt mind upgrading to a beta if it didnt have any bugs. cause in using this version i already got the monitor acting strange, the internet cutting off for no apparent reason.

---

### Post by lavinog on 2010-04-08
> **DonutPower said:**
> well that was the flash package that i found after reading some articles about Ubuntu.  my Dell is 32bit. got the thing in 2002. so its quite old.
How did you install flash?
Did you follow a guide or did you install it with the software center or synaptic?

---

### Post by DonutPower on 2010-04-08
> **lavinog said:**
> How did you install flash?
Did you follow a guide or did you install it with the software center or synaptic?

used a guide that had like the 10 essential software to install. and it was all just commands to key into the terminal and stuff would install. read a few other ones and it was the same instructions. 
whenever i try to use the software center or synaptic i get this lag from the high cpu usage, to where they are unusable, cause the system just locks up momentarily. so i havent been able to actually go and see what packages are available through those cause its such a hassle.

---

### Post by DonutPower on 2010-04-09
is it at all possible that the theme could be whats sucking the RAM?? 

just now i downloaded a dark theme off the net. prior to installing it i had 512MB used up for no reason, once i switched to the theme i downloaded, memory went down to 279MB.

---

### Post by lavinog on 2010-04-09
> **DonutPower said:**
> is it at all possible that the theme could be whats sucking the RAM?? 

just now i downloaded a dark theme off the net. prior to installing it i had 512MB used up for no reason, once i switched to the theme i downloaded, memory went down to 279MB.

It is possible...The theme could be heavy in graphics, or it could have something extra that shouldn't be part of the theme.
Do you have a link to the theme you downloaded.

---

### Post by DonutPower on 2010-04-09
this is the one i downloaded [http://gnome-look.org/content/show.php/Bruzd-Nodoka?content=66332](http://gnome-look.org/content/show.php/Bruzd-Nodoka?content=66332)

before i was using the built in theme called Dust.  cause it was the only dark theme of the default choices. 


memory went up to 411MB now. all im using is Google Chrome to surf the net. and same deal, if i add up all the memory used by the processes running, its total is still under 100MB. 

so still not sure what is sucking up the RAM but i did find it odd how in changing themes, it immediately released like 300MB.

---

### Post by lavinog on 2010-04-09
did you install the Nodoka GTK+ engine?
Did you install it from the link or from the repository?

---

### Post by DonutPower on 2010-04-09
just the theme itself, it does show an error saying that the theme wont look as intended because the required window manager is not installed. i didnt want to go installing anything else cause i didnt want to make this thing work harder than it already is.

i downloaded the file. it was a zip, so i just dragged into the Appearance window , clicked it and hit close. 

i just did a restart with the new theme. and after it loads and is ready to be used, its only taking up 194MB. which to me is how it should always be. 

right now its at 203MB. guessing i should just leave it alone for a while and see if the RAM still gets used up for no reason.

---

