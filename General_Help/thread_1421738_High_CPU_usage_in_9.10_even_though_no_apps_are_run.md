---
title: "High CPU usage in 9.10 even though no apps are running."
date: 2010-03-04
forum: General Help
---

### Post by Antiverminseed on 2010-03-04
Hi, I installed Ubuntu 9.10 Karmic a few weeks ago and been experiencing very high cpu-usage (with no apps running between 40-70, was never that high in previous os). 

I have a Fujitsu Siemes Amilo sa3650 and i installed, manually, the ATI Catalyst 10.2-driver. I figured the problem was either that driver or something with x.org. I'm not the most experienced ubuntu-user but after reading some, that was my conclusion. So I removed my xserver compeletely and installed it again and after that i tried first installing the old ATI catalyst 9.12 but failed miserably and decided to try install ATI catalyst 10.2 again, thinking i might have done something wrong the last time. After discovering the problem was still there i decided to simply ask here on ubuntuforums and trust the ubuntu-spirit to lift me from this miserable state. 

I might have looked in the wrong places, i don't know, but I haven't found any thread with this problem. Some complain about high CPU usage in karmic but they say they have 100% usage, which i have not, so i'm guessing we don't have the same problem.

Does anyone has any ideas of how i can solve this?

---

### Post by doas777 on 2010-03-04
open a terminal (apps -> Accessories -> terminal) and issue this command:
```

top

```

the app using the most CPU should be the one on the top of the list. let us know what it is. 
I assume that this problem persists over a reboot, right? every once in a while I'll have a process spin endlessly for no good reason, and a reboot, or killing the process was all that was required.

---

### Post by Antiverminseed on 2010-03-04
Don't really know what all this means but maybe some of you do:

```
alex@alex-laptop:~$ top

top - 21:31:55 up 29 min,  2 users,  load average: 0.28, 0.31, 0.30
Tasks: 162 total,   8 running, 154 sleeping,   0 stopped,   0 zombie
Cpu(s): 20.4%us, 13.3%sy,  0.0%ni, 65.7%id,  0.0%wa,  0.5%hi,  0.2%si,  0.0%st
Mem:   3796812k total,  1533820k used,  2262992k free,    39304k buffers
Swap: 11124972k total,        0k used, 11124972k free,   425624k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4525 root      20   0  231m  86m  28m R   14  2.3   2:19.71 Xorg               
  661 root      18  -2 17448 1340  308 S    8  0.0   1:45.40 udevd              
  849 messageb  20   0 24260 1920  792 R    5  0.1   1:22.61 dbus-daemon        
 7019 root      20   0 42432 3028 2376 R    5  0.1   2:08.25 devkit-disks-da    
12897 alex      20   0  547m 105m  27m S    3  2.8   2:30.81 firefox            
13569 alex      20   0  212m  15m  10m S    3  0.4   0:01.14 gnome-terminal     
 6973 alex      20   0  186m  13m 9552 R    3  0.4   0:33.49 update-notifier    
 6795 alex      20   0  246m  33m 9012 S    2  0.9   0:09.31 compiz.real        
 7189 alex      20   0 54908 3808 2632 S    2  0.1   0:45.71 gvfs-gdu-volume    
21293 alex      20   0  104m  13m 9964 S    2  0.4   0:21.28 npviewer.bin       
   43 root      15  -5     0    0    0 S    2  0.0   0:10.91 scsi_eh_1          
 6247 alex      20   0  201m 5040 3520 S    1  0.1   0:08.06 pulseaudio         
 6978 alex      20   0  157m 8204 5908 R    1  0.2   0:42.20 gdu-notificatio    
  466 root      20   0 12768  832  560 S    1  0.0   0:18.86 upstart-udev-br    
13678 alex      20   0 19132 1360  980 R    1  0.0   0:00.33 top                
    1 root      20   0 19424 1820 1196 S    0  0.0   0:21.15 init               
   10 root      15  -5     0    0    0 S    0  0.0   0:02.12 events/1           
 5867 root      20   0  215m  47m  25m S    0  1.3   0:06.24 synaptic           
 6312 alex      20   0  299m  10m 7564 S    0  0.3   0:01.23 gnome-settings-    
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd
```What is id and why is it abnormally high?

---

### Post by Antiverminseed on 2010-03-04
> **doas777 said:**
> open a terminal (apps -> Accessories -> terminal) and issue this command:
```

top

```the app using the most CPU should be the one on the top of the list. let us know what it is. 
I assume that this problem persists over a reboot, right? every once in a while I'll have a process spin endlessly for no good reason, and a reboot, or killing the process was all that was required.


Yes, it does persist after reboot. 

Also, I just now installed xorg and ati 10.2 so i'm not sure, but before when running 10.2 my computer sometimes had problems loading os when booting it. Every other time i turned it on i could here the ubuntu-drums but ended up with a black screen. Don't know if this is related, but that was really the main reason i thought something was wrong with my graphic drivers, or something of that nature.

---

### Post by Antiverminseed on 2010-03-04
> **doas777 said:**
> open a terminal (apps -> Accessories -> terminal) and issue this command:
```

top

```the app using the most CPU should be the one on the top of the list. let us know what it is. 
I assume that this problem persists over a reboot, right? every once in a while I'll have a process spin endlessly for no good reason, and a reboot, or killing the process was all that was required.

```
alex@alex-laptop:~$ top

top - 21:47:26 up 45 min,  2 users,  load average: 0.32, 0.37, 0.35
Tasks: 161 total,   1 running, 160 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.0%us,  7.8%sy,  0.0%ni, 80.9%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   3796812k total,  1618704k used,  2178108k free,    40424k buffers
Swap: 11124972k total,        0k used, 11124972k free,   434060k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4525 root      20   0  232m  87m  28m S   12  2.4   3:44.56 Xorg               
13569 alex      20   0  214m  16m  10m S    4  0.4   0:04.84 gnome-terminal     
  661 root      18  -2 17448 1340  308 S    3  0.0   2:43.57 udevd              
12897 alex      20   0  575m 103m  28m S    3  2.8   3:57.47 firefox            
21293 alex      20   0  104m  13m 9964 S    2  0.4   0:36.57 npviewer.bin       
  849 messageb  20   0 24260 1920  792 S    2  0.1   2:09.53 dbus-daemon        
 7019 root      20   0 42460 3056 2376 S    2  0.1   3:19.77 devkit-disks-da    
 6978 alex      20   0  157m 8544 5908 S    1  0.2   1:05.03 gdu-notificatio    
  779 root      15  -5     0    0    0 S    1  0.0   0:01.00 phy0               
  923 haldaemo  20   0 34140 4660 3600 S    1  0.1   0:14.06 hald               
 6795 alex      20   0  246m  33m 9064 S    1  0.9   0:11.99 compiz.real        
 6973 alex      20   0  186m  14m 9552 S    1  0.4   0:52.20 update-notifier    
13678 alex      20   0 19132 1364  980 R    1  0.0   0:06.26 top                
    1 root      20   0 19424 1820 1196 S    0  0.0   0:32.48 init               
   43 root      15  -5     0    0    0 S    0  0.0   0:17.49 scsi_eh_1          
  466 root      20   0 12768  832  560 S    0  0.0   0:29.71 upstart-udev-br    
 7189 alex      20   0 55296 4144 2632 S    0  0.1   1:12.39 gvfs-gdu-volume    
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.12 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        

```

---

### Post by doas777 on 2010-03-04
well,according to top, you are using more cpu that I would expect from those processes, but not near 100%.
the gnome-system-monitor application has a bad habit of exagerating usage figures, and the rendering of the graphs on the third tab, in itself can take up significant cpu (15-50%). thats why I recommended top. 

it looks like your xorg process is taking up the most clock in our top output, but why may be beyond me. your suspicion about the driver may be well warranted. can use use the ubuntu ati driver, or do you have to install it from ati? wherever you got the one you are using, try the other one.

---

### Post by rnerwein on 2010-03-04
> **Antiverminseed said:**
> ```
alex@alex-laptop:~$ top

top - 21:47:26 up 45 min,  2 users,  load average: 0.32, 0.37, 0.35
Tasks: 161 total,   1 running, 160 sleeping,   0 stopped,   0 zombie
Cpu(s): 11.0%us,  7.8%sy,  0.0%ni, 80.9%id,  0.0%wa,  0.0%hi,  0.3%si,  0.0%st
Mem:   3796812k total,  1618704k used,  2178108k free,    40424k buffers
Swap: 11124972k total,        0k used, 11124972k free,   434060k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 4525 root      20   0  232m  87m  28m S   12  2.4   3:44.56 Xorg               
13569 alex      20   0  214m  16m  10m S    4  0.4   0:04.84 gnome-terminal     
  661 root      18  -2 17448 1340  308 S    3  0.0   2:43.57 udevd              
12897 alex      20   0  575m 103m  28m S    3  2.8   3:57.47 firefox            
21293 alex      20   0  104m  13m 9964 S    2  0.4   0:36.57 npviewer.bin       
  849 messageb  20   0 24260 1920  792 S    2  0.1   2:09.53 dbus-daemon        
 7019 root      20   0 42460 3056 2376 S    2  0.1   3:19.77 devkit-disks-da    
 6978 alex      20   0  157m 8544 5908 S    1  0.2   1:05.03 gdu-notificatio    
  779 root      15  -5     0    0    0 S    1  0.0   0:01.00 phy0               
  923 haldaemo  20   0 34140 4660 3600 S    1  0.1   0:14.06 hald               
 6795 alex      20   0  246m  33m 9064 S    1  0.9   0:11.99 compiz.real        
 6973 alex      20   0  186m  14m 9552 S    1  0.4   0:52.20 update-notifier    
13678 alex      20   0 19132 1364  980 R    1  0.0   0:06.26 top                
    1 root      20   0 19424 1820 1196 S    0  0.0   0:32.48 init               
   43 root      15  -5     0    0    0 S    0  0.0   0:17.49 scsi_eh_1          
  466 root      20   0 12768  832  560 S    0  0.0   0:29.71 upstart-udev-br    
 7189 alex      20   0 55296 4144 2632 S    0  0.1   1:12.39 gvfs-gdu-volume    
    2 root      15  -5     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT  -5     0    0    0 S    0  0.0   0:00.12 migration/0        
    4 root      15  -5     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        

```

hi
oh for get it you post just another output of top.
sorry
ciao

---

### Post by Antiverminseed on 2010-03-04
> **rnerwein said:**
> hi
oh for get it you post just another output of top.
sorry
ciao

Yeah, sorry about that i forgot to quote the other user before so i did it all over again.

---

### Post by Antiverminseed on 2010-03-04
> **doas777 said:**
> well,according to top, you are using more cpu that I would expect from those processes, but not near 100%.
the gnome-system-monitor application has a bad habit of exagerating usage figures, and the rendering of the graphs on the third tab, in itself can take up significant cpu (15-50%). thats why I recommended top. 

it looks like your xorg process is taking up the most clock in our top output, but why may be beyond me. your suspicion about the driver may be well warranted. can use use the ubuntu ati driver, or do you have to install it from ati? wherever you got the one you are using, try the other one.

ok, yeah, thanks i thought about that but i have tried avoiding it cause' i'm running one of the few laptops that comes with a so called "graphic booster" ([http://ts.fujitsu.com/home/products/notebooks/amilo_sa_3650.html](http://ts.fujitsu.com/home/products/notebooks/amilo_sa_3650.html)) and i haven't tried using it with ubuntu yet but i fear it probably takes the regular ATI-driver to use it. 

Well, you're probably right; might as well try another driver. 

Read something about EnvyNG. Might look into that. 

Thanks for trying!

---

### Post by no2498 on 2010-03-04
i did not see any thing bad my self on your computer

but if it runs hot or the memory spikes if you do open any thing
try this
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to (  x window system (no xv)
write down what its set on
you can change it back the same way if it does not help
you may need to restart the computer before you see what it does
you may also need to install gstreamer just go to add/remove and install it

hope that helps

---

### Post by Antiverminseed on 2010-03-05
> **no2498 said:**
> i did not see any thing bad my self on your computer

but if it runs hot or the memory spikes if you do open any thing
try this
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to (  x window system (no xv)
write down what its set on
you can change it back the same way if it does not help
you may need to restart the computer before you see what it does
you may also need to install gstreamer just go to add/remove and install it

hope that helps

I could now just barely start up my OS at all. Something's wrong clearly. I get a black screen but with the cursor intact. I press ctrl + alt + F1 and the screen gets covered with big red and green pixels. AFter shutting it down, manually, and booting it again five or six times i finally get in to OS. 

It was set on "identify automatically"

Edit: I asked about gstreamer but I realized now what it is after doing the command :P

---

### Post by Antiverminseed on 2010-03-05
> **no2498 said:**
> i did not see any thing bad my self on your computer

but if it runs hot or the memory spikes if you do open any thing
try this
open a terminal type ( gstreamer-properties ) click enter
click video set the plugin to (  x window system (no xv)
write down what its set on
you can change it back the same way if it does not help
you may need to restart the computer before you see what it does
you may also need to install gstreamer just go to add/remove and install it

hope that helps

I rebooted, but the problem remains. At least the high cpu usage. It did start up properly but then again it usually does after a reboot, it's when i shut it down and then boot it the problem appears.

---

### Post by Houchy on 2010-05-24
Hi,

I have the same problem with the same laptop, CPU running high in % and also temperature around 65°C even with no application running.

Did you manage to solve it?

Did you manage to use the graphicbooster? on my side, the HD 3870 is not recognized. Any luck on your side?

Thank you.

---

### Post by Antiverminseed on 2010-05-24
> **Houchy said:**
> Hi,

I have the same problem with the same laptop, CPU running high in % and also temperature around 65°C even with no application running.

Did you manage to solve it?

Did you manage to use the graphicbooster? on my side, the HD 3870 is not recognized. Any luck on your side?

Thank you.

i didn't quite figure it out actually. It ended with me switching to Windows 7. But i do think you can fix it. I was given some help in a swedish forum. I could try translating it. I really don't have time right now but later on I could give it a shot. 

i did manage to use the graphic booster though. i just installed, from the ATI-homepage, the latest driver and CCC available for ubuntu and it worked. It did take a lot of rebooting everytime I plugged it in though.

Why the Fujitsu Siemens amilo sa3650 is so warm is probably because of some major fault in construction and/or the fans. Theres no OS-solution to that problem. There is some kind of cooling-device you can use though, i've been thinking about getting one myself after my friend told me about it.

---

### Post by Failboat88 on 2010-05-24
ATI and Linux suck together. What was it like before you used proprietary drivers? I use the open-source ones and they work for the most part. Compiz cube doesn't work, and certain animations make my pc go so slow it almost crashes.

---

### Post by Antiverminseed on 2010-05-24
> **Failboat88 said:**
> ATI and Linux suck together. What was it like before you used proprietary drivers? I use the open-source ones and they work for the most part. Compiz cube doesn't work, and certain animations make my pc go so slow it almost crashes.

i never used open source. I did try an older version of the proprietary driver but it didn't work any better so I reinstalled the latest again.

---

### Post by Failboat88 on 2010-05-25
When you first booted into your desktop that was you using the open-source driver. You could use your cd to try the live version and see if things work. If things do work as intended try and get your real OS off the proprietary drivers or just reformat.

---

### Post by Antiverminseed on 2010-05-25
> **Failboat88 said:**
> When you first booted into your desktop that was you using the open-source driver. You could use your cd to try the live version and see if things work. If things do work as intended try and get your real OS off the proprietary drivers or just reformat.

Oh right of course :P Naturally it was open source when i first installed it i just didn't think of it when i wrote the last post. I did have problems with the open source as well though which was why tried the proprietary to begin with. I

---

