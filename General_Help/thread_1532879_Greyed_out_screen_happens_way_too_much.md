---
title: "Greyed out screen happens way too much"
date: 2010-07-17
forum: General Help
---

### Post by Jacksie on 2010-07-17
I've searched for this a fair bit but everyone seems to have a different cause.

I constantly get applications greyed out. (I understand this is when ubuntu sees them as 'not responding') It happens to Firefox a lot, but that may just be because I use it alot. It happens to Nautilus a lot too, and sometimes the everything gets grey at once.

Windows, every other OS I've ever had installed (including older Ubuntus) and the 10.04 live-cd all run fine. So I'm under the impression that it's something either that i've installed or that ubuntu did when it installed. 

It's done this pretty regularly from day one, so it doesn't seem to be something I've done lol.

What possible causes are there for this? Is there a log or something I can check that may enlighten me?

---

### Post by Rubi1200 on 2010-07-17
First try something like this:

Go to Applications > Accessories > Terminal and run the following:

```
firefox
```

```
nautilus
```

```
lspci | grep VGA
```

Run them separately obviously. The first 2 are to see if you get any error messages and the last one is to find out what type of graphics card you have.

Post the relevant results back here please.

---

### Post by Jacksie on 2010-07-17
Already tried a few programs that have done it in terminal like that. No errors or anything.

lspci | grep VGA just gave me

```
01:00.0 VGA compatible controller: ATI Technologies Inc RV770 [Radeon HD 4870]

```

---

### Post by Rubi1200 on 2010-07-17
When you browse to the folder /var/crash is there anything in there?

---

### Post by Jacksie on 2010-07-17
Nope, empty.

---

### Post by Rubi1200 on 2010-07-17
Ok,

1. so you have the ATI Radeon; are the drivers for it also installed?

2. are desktop effects turned on?

3. do you use a screensaver (one of the defaults or downloaded and installed)?

4. can you post the output of this please:

```
top
```

---

### Post by Jacksie on 2010-07-17
Yep, proprietary drivers are installed. Desktop effects are set to 'normal'.

No screensaver, just set monitor to standby when idle for 5 minutes.


```

top - 18:48:08 up 57 min,  2 users,  load average: 0.42, 0.52, 0.52
Tasks: 168 total,   1 running, 166 sleeping,   0 stopped,   1 zombie
Cpu(s):  2.8%us,  0.3%sy,  0.0%ni, 96.5%id,  0.3%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4120620k total,  1105672k used,  3014948k free,   142304k buffers
Swap:  3905528k total,        0k used,  3905528k free,   437156k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1197 root      20   0  175m 122m  24m S    2  3.0   1:45.68 Xorg               
 2033 quinn     20   0  151m  54m  25m S    1  1.3   0:52.85 codeblocks         
 2794 quinn     20   0 64464  14m  10m S    1  0.4   0:00.48 gnome-terminal     
 1896 quinn     20   0  285m  61m  30m S    1  1.5   0:40.22 rhythmbox          
   26 root      20   0     0    0    0 S    0  0.0   0:00.37 ata/0              
  285 root      20   0     0    0    0 S    0  0.0   0:00.60 scsi_eh_4          
 1451 quinn      9 -11  159m  11m 9284 S    0  0.3   0:10.34 pulseaudio         
 2813 quinn     20   0  2544 1212  904 R    0  0.0   0:00.08 top                
    1 root      20   0  2800 1640 1188 S    0  0.0   0:00.31 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 events/0           
   10 root      20   0     0    0    0 S    0  0.0   0:00.35 events/1           
   11 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   12 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   14 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr          
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                 
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers        
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default        
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   21 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/0          
```

---

### Post by Rubi1200 on 2010-07-17
Well, this is a mystery.

The only thing I can think of right now is to turn desktop effects off and see if that makes a difference.

System > Preferences > Appearance > Visual Effects and set it to None.

I see you have codeblocks installed and running; just grabbing at straws here, but do these grey screens happen when you are _not_ using it?

---

### Post by Jacksie on 2010-07-17
I'd have to pay more attention, but I haven't had one since I started this thread and I did open Code::Blocks around the same time. It's the (old) 8.02 version from the repository if that matters.

Will try turning visual effects off.

---

### Post by Rubi1200 on 2010-07-17
Ok, good luck!

Clearly, something must be causing this; memory, CPU issues?

If I find anything else about this I'll post back, but for the moment I am out of ideas.

---

