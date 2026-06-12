---
title: "Bad performance"
date: 2010-08-31
forum: General Help
---

### Post by JoeTheDude on 2010-08-31
Just installed 10.04 to my newer computer because my older one was having issues (Some ATI problem I presumed). Now I'm getting worse GUI performance than I was on my older computer, especially with Compiz on. Low framerate and bad screen tearing. Specs:

Intel Core i5-750
nVidia GeForce 8800GT
MSI P55M-GD45 mobo
4GB DDR3 RAM @ 800Mhz

I installed the "recommended" nVidia proprietary drivers and got no performance increase. So I'm stuck. About to just give up on Linux and go back to Windows. Help?

PS - I apologize if I've come across as a cranky old man.

---

### Post by an0dos on 2010-08-31
> **JoeTheDude said:**
> Just installed 10.04 to my newer computer because my older one was having issues (Some ATI problem I presumed). Now I'm getting worse GUI performance than I was on my older computer, especially with Compiz on. Low framerate and bad screen tearing. Specs:

Intel Core i5-750
nVidia GeForce 8800GT
MSI P55M-GD45 mobo
4GB DDR3 RAM @ 800Mhz

I installed the "recommended" nVidia proprietary drivers and got no performance increase. So I'm stuck. About to just give up on Linux and go back to Windows. Help?

PS - I apologize if I've come across as a cranky old man.

Did you disable kms per the directions in the release notes on the wiki?
You should also blacklist the nouveau drivers as follows:
```
gksudo gedit /etc/modprobe.d/blacklist.conf
```
And add ```
blacklist nouveau
``` at the bottom of the list.

Then reinstall the nvidia driver by deactivating it through 'hardware drivers' and re-enabling it once you complete the above steps. Also make sure you activate the 256 driver and not the 173 driver.

---

### Post by JoeTheDude on 2010-08-31
Thanks for the reply.

I've done everything you mentioned and am still having sluggish performance.

---

### Post by an0dos on 2010-08-31
> **JoeTheDude said:**
> Thanks for the reply.

I've done everything you mentioned and am still having sluggish performance.

Backup your xorg.conf, then delete the original version and run ```
sudo nvidia-xconfig
```

Then reboot your computer.

---

### Post by JoeTheDude on 2010-08-31
> **an0dos said:**
> Backup your xorg.conf, then delete the original version and run ```
sudo nvidia-xconfig
```Then reboot your computer.

No change :(

---

### Post by philinux on 2010-08-31
What do the following commands show.

```
top
```

```
free -m
```

---

### Post by JoeTheDude on 2010-08-31
top shows:

```

top - 08:18:43 up 14 min,  2 users,  load average: 0.56, 0.37, 0.25
Tasks: 187 total,   2 running, 185 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.7%us,  0.5%sy,  0.0%ni, 97.8%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4109452k total,   633076k used,  3476376k free,    36940k buffers
Swap:  3905528k total,        0k used,  3905528k free,   281832k cached
top - 08:19:18 up 15 min,  2 users,  load average: 0.39, 0.35, 0.24
Tasks: 187 total,   1 running, 186 sleeping,   0 stopped,   0 zombie
Cpu(s):  4.1%us,  0.9%sy,  0.0%ni, 94.4%id,  0.6%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   4109452k total,   633860k used,  3475592k free,    37156k buffers
Swap:  3905528k total,        0k used,  3905528k free,   281912k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
 1803 chaosene  20   0 71548  14m  10m S    9  0.4   0:00.71 gnome-terminal     
 1222 root      20   0 62180  48m  14m S    2  1.2   0:12.30 Xorg               
 1538 chaosene  20   0 61296  47m  15m S    2  1.2   0:04.05 compiz             
 1678 chaosene  20   0  266m  57m  19m S    2  1.4   0:15.93 plugin-containe    
 1527 chaosene   9 -11  156m 5592 4424 S    1  0.1   0:09.97 pulseaudio         
 1650 chaosene  20   0  244m  66m  26m S    1  1.7   0:20.43 firefox-bin        
 1821 chaosene  20   0  2548 1244  916 R    1  0.0   0:00.12 top                
   38 root      20   0     0    0    0 S    0  0.0   0:00.18 ata/0              
 1516 chaosene  20   0 88988 9180 7080 S    0  0.2   0:00.15 gnome-settings-    
 1582 chaosene  20   0 38616  12m 9956 S    0  0.3   0:00.24 wnck-applet        
 1596 chaosene  20   0 20256 9600 7728 S    0  0.2   0:00.17 gtk-window-deco    
    1 root      20   0  2800 1652 1208 S    0  0.0   0:00.54 init               
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1        
    7 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1        
    8 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1         
    9 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2        
   10 root      20   0     0    0    0 S    0  0.0   0:00.01 ksoftirqd/2        
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2         
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/3        
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/3        
   14 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/3         
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 events/0           
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 events/1           
   17 root      20   0     0    0    0 S    0  0.0   0:00.00 events/2           
   18 root      20   0     0    0    0 S    0  0.0   0:00.00 events/3           
   19 root      20   0     0    0    0 S    0  0.0   0:00.00 cpuset             
   20 root      20   0     0    0    0 S    0  0.0   0:00.00 khelper            
   21 root      20   0     0    0    0 S    0  0.0   0:00.00 netns              
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 async/mgr          
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 pm                 
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers        
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default        
   27 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/0      
   28 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/1      
   29 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/2      
   30 root      20   0     0    0    0 S    0  0.0   0:00.00 kintegrityd/3      
   31 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/0          
   32 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/1          
   33 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/2          
   34 root      20   0     0    0    0 S    0  0.0   0:00.00 kblockd/3          
   35 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpid             
   36 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_notify       
   37 root      20   0     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug      
   39 root      20   0     0    0    0 S    0  0.0   0:00.02 ata/1    

```

free -m shows:

```

             total       used       free     shared    buffers     cached
Mem:          4013        624       3388          0         36        280
-/+ buffers/cache:        307       3705
Swap:         3813          0       3813

```

---

### Post by realzippy on 2010-08-31
When having problems with nvidia it is a good idea to create the nvidia-log file:

```
sudo nvidia-bug-report.sh
```

Can you post that file please?

---

### Post by JoeTheDude on 2010-08-31
Here you are.

---

### Post by realzippy on 2010-08-31
...nothing special in the file.

[I]Connected display device(s) on GeForce 8800 GT at PCI:1:0:0:
(--) Aug 31 08:04:05 NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) Aug 31 08:04:05 NVIDIA(0):     LG TV (DFP-1)[/I]

So you have 2 displays connected?
If so,have you configured them with nvidia-settings?
(According to your* xorg.conf* you did not....  ?)
If so,does unplugging the LG TV help?

---

### Post by JoeTheDude on 2010-08-31
> **realzippy said:**
> ...nothing special in the file.

[I]Connected display device(s) on GeForce 8800 GT at PCI:1:0:0:
(--) Aug 31 08:04:05 NVIDIA(0):     Samsung SyncMaster (DFP-0)
(--) Aug 31 08:04:05 NVIDIA(0):     LG TV (DFP-1)[/I]

So you have 2 displays connected?
If so,have you configured them with nvidia-settings?
(According to your* xorg.conf* you did not....  ?)
If so,does unplugging the LG TV help?

I didn't really configure anything... just left the TV display disabled (I only use it on occasion). I went ahead and unplugged the TV and restarted. No change.

What is it exactly I need to configure? All the defaults in the nVidia X Server Settings seemed fine. Is there something else I'm missing?

---

### Post by realzippy on 2010-08-31
You could try;

```
gksudo nvidia-settings
```

Then hit "Save To X Configuration File"

then restartX or reboot.Don`t think it will help,but it does no harm.The *xorg.conf* might be different afterwards (xinerama section added..)

Restarting compiz might be an idea:

```
compiz --replace
```

any changes?

---

### Post by JoeTheDude on 2010-08-31
> **realzippy said:**
> You could try;

```
gksudo nvidia-settings
```Then hit "Save To X Configuration File"

then restartX or reboot.Don`t think it will help,but it does no harm.The *xorg.conf* might be different afterwards (xinerama section added..)

Restarting compiz might be an idea:

```
compiz --replace
```any changes?

Well I don't know which of these did it, but it's running great now. Perfectly smooth.

Thanks so much everyone! Maybe I won't have to go back to Windows after all :p

---

### Post by realzippy on 2010-08-31
If it was

```
compiz --replace
```

it will not survive a reboot...

If this happens,simply put

compiz --replace

in the Startup Applications...


...and please mark thread as solved (Threadtools)

---

### Post by JoeTheDude on 2010-08-31
> **realzippy said:**
> If it was

```
compiz --replace
```it will not survive a reboot...

If this happens,simply put

compiz --replace

in the Startup Applications...


...and please mark thread as solved (Threadtools)

Ah okay, thanks very much guys.

---

### Post by JoeTheDude on 2010-08-31
Shoot... sorry guys. As soon as I restarted, the problem returned even though I added the "compiz --replace" command to Startup Applications. I tried manually entering it as well, but it still didn't help. I backtracked and tried other things in this thread again and nothing fixed it.

So... the problem persists. :(

---

### Post by realzippy on 2010-08-31
....may be wrong,but think it might be a compiz problem rather than a nvidia issue.Do you have [CCSM]("http://wiki.compiz.org/CCSM") installed?
Did you enable compiz by desktoprightclick/effects  ?
Is metacity working fine?

---

### Post by JoeTheDude on 2010-08-31
> **realzippy said:**
> ....may be wrong,but think it might be a compiz problem rather than a nvidia issue.Do you have [CCSM]("http://wiki.compiz.org/CCSM") installed?
Did you enable compiz by desktoprightclick/effects  ?
Is metacity working fine?

Yes I use CCSM to configure Compiz and also have max effects enabled in appearance preferences. Metacity seems to be working fine... the only issue really is just low FPS in Compiz, really jittery.

---

### Post by realzippy on 2010-09-01
I suggest to reinstall compiz:

delete "compiz --replace" temporarily from your Startup Applications.

Then:

```
nohup metacity --replace &
```

stops compiz.


```
gconftool-2 --recursive-unset /apps/compiz
rm -rf ~/.compiz 
```

resets compiz and deletes compiz config.

Then *reinstall* all compiz packages with synaptic,restart X.
Do not set visual effects by rightclickdesktop-tool,make settings only with CCSM.

---

### Post by JoeTheDude on 2010-09-01
> **realzippy said:**
> I suggest to reinstall compiz:

delete "compiz --replace" temporarily from your Startup Applications.

Then:

```
nohup metacity --replace &
```

stops compiz.


```
gconftool-2 --recursive-unset /apps/compiz
rm -rf ~/.compiz 
```

resets compiz and deletes compiz config.

Then *reinstall* all compiz packages with synaptic,restart X.
Do not set visual effects by rightclickdesktop-tool,make settings only with CCSM.

Reinstalled everything, same bad performance :frown:

Is the 8800GT just not a good card for Compiz or something? My old ATI x1600 ran it perfectly (aside from locking up every 15 minutes for some unknown reason).

---

### Post by realzippy on 2010-09-01
...strange that it used to run once.

---

### Post by JoeTheDude on 2010-09-01
> **realzippy said:**
> ...strange that it used to run once.

Baffling, indeed.

---

### Post by realzippy on 2010-09-01
Install *fusion-icon* and switch metacity/compiz with the
*--loose-binding* option...

---

### Post by JoeTheDude on 2010-09-01
> **realzippy said:**
> Install *fusion-icon* and switch metacity/compiz with the
*--loose-binding* option...

Hmmmm, doesn't seem to have done anything.

---

### Post by realzippy on 2010-09-01
reloading nvidia-settings ?

```
nvidia-settings -l
```

---

### Post by JoeTheDude on 2010-09-01
> **realzippy said:**
> reloading nvidia-settings ?

```
nvidia-settings -l
```

Nothing.

---

### Post by realzippy on 2010-09-01
To simulate the situation when it used to work
(but you might have tested this already?):

Delete current xorg.conf:

```
sudo rm /etc/X11/xorg.conf
```

make a vanilla one:

```
sudo nvidia-xconfig
```

reboot to load this.Then:

[gksudo nvidi.... same as you did in post 11]("http://ubuntuforums.org/showpost.php?p=9788650&postcount=12")

---

### Post by JoeTheDude on 2010-09-01
> **realzippy said:**
> To simulate the situation when it used to work
(but you might have tested this already?):

Delete current xorg.conf:

```
sudo rm /etc/X11/xorg.conf
```

make a vanilla one:

```
sudo nvidia-xconfig
```

reboot to load this.Then:

[gksudo nvidi.... same as you did in post 11]("http://ubuntuforums.org/showpost.php?p=9788650&postcount=12")

Yeah, I had already retried it, but I decided to do it again just for kicks. Still the same bad framerate. I don't know how it managed to work that one time... guess my computer immunized itself from this fix :-?

---

### Post by realzippy on 2010-09-01
Something must have been different...have you replugged 2nd monitor meanwhile?
Can you post current xorg.conf to compare with very 1rst from bug.report...

---

### Post by JoeTheDude on 2010-09-01
No, the other display is still unplugged.

Here's both my current xorg and the backup I originally made near the beginning of this thread.

---

### Post by realzippy on 2010-09-01
Section "Module"
	Load	"glx"
EndSection


is missing in the current.Don't think it will,but give it a try.

---

### Post by JoeTheDude on 2010-09-01
> **realzippy said:**
> Section "Module"
	Load	"glx"
EndSection


is missing in the current.Don't think it will,but give it a try.

Nope, adding it and rebooting didn't change anything.

---

### Post by realzippy on 2010-09-01
Then test with compiz itself:
Resetting compiz to defaults in CCSM...
Testing the inauspicious compiz activating right-click/desktopeffects tool again..
Testing emerald window decorator instead of GTK...
   [I]sudo apt-get install emerald && emerald --replace

[/I]
Testing the CCSM "Workaround" options..
I would refuse to give up knowing that it used to work once..

BTW,reminds me of my very first ubuntu experience.Took days,but it is worth it..dunno
how often I reinstalled only because I smashed my desktop effects.

---

### Post by JoeTheDude on 2010-09-01
> **realzippy said:**
> Then test with compiz itself:
Resetting compiz to defaults in CCSM...
Testing the inauspicious compiz activating right-click/desktopeffects tool again..
Testing emerald window decorator instead of GTK...
   [I]sudo apt-get install emerald && emerald --replace

[/I]
Testing the CCSM "Workaround" options..
I would refuse to give up knowing that it used to work once..

BTW,reminds me of my very first ubuntu experience.Took days,but it is worth it..dunno
how often I reinstalled only because I smashed my desktop effects.

I think I'm just going to reformat and reinstall Ubuntu so I can start from the beginning again. Thanks for all the help, I really appreciate it. I'll post again sometime later with an update on how things are working.

---

### Post by JoeTheDude on 2010-09-01
Well I give up. I'm just going to deal with the slowness. It's not really *that* bad I guess.

I don't consider this solved by any means but for anyone else who has this kind of problem, there is about a one in five chance this will fix it until you reboot:

1. gksudo nvidia-settings
2. Change the resolution and apply
3. Change it back and apply (make sure to set '60hz', not 'Auto')
4. Save to X config
5. Save nVidia config
6. Quit and open terminal
7. compiz --replace
8. Hopefully it works

Don't know why this method is so inconsistent but the fact that it works sometimes is better than never I guess.

---

### Post by realzippy on 2010-09-02
*Don't know why this method is so inconsistent but the fact that it works sometimes is better than never I guess....*


Some time ago I had also a strange issue:
FSAA which I set in nvidia-settings did not "survive" a reboot...
it was of course still marked as "enabled" but not working.
It only worked when I turned the computer off for a few seconds
(PSU completely off) and did a "cold" boot.Don`t know why this happened,
can only guess ...however,this issue disappeared since Lucid.

---

### Post by JoeTheDude on 2010-09-03
Just randomly came across a permanent fix! I was messing around with the Compiz general settings and unticked 'Detect Refresh Rate'. Performance is smooth as a baby's butt now.

Something is wrong with Compiz's refresh rate detection I guess. I opened up the benchmark tool and found Compiz had my framerate locked at 30 until I applied the above changes. Now it's a consistent 60 fps.

Solved.

---

