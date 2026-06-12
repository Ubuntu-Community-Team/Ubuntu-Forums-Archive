---
title: "External HD Unresponsive After Long Idleness"
date: 2010-01-30
forum: General Help
---

### Post by angheloko on 2010-01-30
Hi All,

First thing, my experience with Ubuntu has been wonderful. I am a Windows user since birth and only started using Ubuntu when Karmic came. My thanks and awe for all that contributed to its success, especially to its community.

Now for the problem. I just bought a 1TB external HD where I horde loads of data and most of the time I keep it plugged into my laptop (which I seldom turn off). However I have noticed that after a long time of idleness, say 7 hrs or so, I could no longer access the external HD and the whole system starts to become unresponsive (Nautilus, System Manager). It just does nothing.

I tried unmounting it graphically and also thru the terminal. Umount'ing it from the terminal gave me this:

```
angheloko@navi:~$ umount /media/Sophia 
Unmount failed: Cannot unmount because file system on device is busy
angheloko@navi:~$ 

```Then I tried an fuser (fuser -m) but the command doesn't return to the prompt.

It happens everytime I leave my machines idle for a long time. Usually I'd just have to restart everything, which is not a biggie but is a tad uncomfortable. I fear that this process might lead to some FS corruption or some bad sectors.

Additionally, this doesn't happen to a 500 GB external HD.

Hoping to see anything suspicious I checked top. Here is the result:
```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
25586 anghelok  20   0  564m 127m  34m S   14  4.2 140:22.85 firefox            
 1221 root      20   0  136m  76m  34m S    9  2.5 132:52.32 Xorg               
 2176 anghelok  20   0  219m 6836 5632 S    3  0.2  30:02.41 pulseaudio         
 5141 anghelok  20   0 45884  13m  10m S    3  0.4   0:15.67 gnome-terminal     
 2300 anghelok  20   0  143m  53m 7412 S    1  1.8  19:31.01 compiz.real        
 2659 anghelok  20   0  114m  27m  12m S    1  0.9  17:04.68 transmission       
11086 anghelok  20   0  2472 1212  884 R    1  0.0   0:00.10 top                
    7 root      15  -5     0    0    0 S    0  0.0   3:53.19 ksoftirqd/1        
   51 root      15  -5     0    0    0 S    0  0.0   0:50.76 scsi_eh_3          
 2154 anghelok  20   0  280m  86m  28m S    0  2.9  15:56.95 banshee-1          
 2301 anghelok  20   0 58508  28m  14m S    0  0.9   4:48.78 gnome-panel        
 2311 anghelok  20   0 71188  28m  17m S    0  0.9   0:07.82 beagle-search      
 2877 anghelok  20   0  181m  53m  24m S    0  1.8   1:50.07 evolution          
10432 anghelok  20   0 80200  34m  21m S    0  1.2   0:43.86 tomboy             
11952 anghelok  20   0 30392  17m 4032 S    0  0.6   4:11.80 ubuntuone-syncd    
12752 anghelok  20   0 71024  36m  12m S    0  1.2   0:19.38 python             
20963 anghelok  20   0  171m  30m  19m S    0  1.0   1:10.51 empathy           
```I tried opening System Monitor but it hangs then I tried Nautilus. Still nothing.

Output from ps shows that Nautilus and System Monitor is running but it's not accessible (Their windows is not showing):

```
angheloko@navi:~$ ps -ef | grep nau
1000      2304  2125  0 Jan29 ?        00:09:43 nautilus
1000     11099     1  0 10:17 ?        00:00:00 nautilus --no-desktop /home/angheloko
1000     11102 25913  0 10:18 pts/2    00:00:00 grep --color=auto nau

``````
angheloko@navi:~$ ps -ef | grep gnome-sys
1000     11090     1  0 10:15 ?        00:00:00 gnome-system-monitor
angheloko@navi:~$ 

```Hope someone could provide me with some answers.

Thanks!

Additional Info:

Turning off the external HD will show the following:

```

Unable to unmount Sophia

DBus error
org.gtk.Private.RemoveVolumeMonitor.NotFound: The given mount was not found
```

Then everything becomes responsive again. Nautilus and System Monitor started to open.

Lastly, the HD has 2 partitions - 500GB each, Sophia - Ext3 and Athena - NTFS

---

### Post by quixote on 2010-01-31
I haven't done anywhere near the exhaustive diagnostics that you've done, but I've noticed similar unresponsiveness, in my case of the system, or maybe primary (only) drive.  It seems to be associated with nautilus losing its tiny mind after the screensaver kicks in (?) or when the system suspends on its own (eg after long inactivity).

I usually just restart, but it doesn't happen very often.  Maybe you could try killing any nautilus process and see if that wakes things up?```
ps -A *[to get a list of all processes]*
sudo kill -9 [PID for any nautilus processes that show up]
```

e.g.: output relevant to nautilus from ps -A:  
4163 ?        00:10:03 nautilus
sudo kill -9 4163

---

