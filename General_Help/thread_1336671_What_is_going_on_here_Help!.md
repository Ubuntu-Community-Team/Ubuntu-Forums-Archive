---
title: "What is going on here?? Help!"
date: 2009-11-24
forum: General Help
---

### Post by cguy on 2009-11-24
USING KARMIC, updated yesterday.

sda1, where /home is also located, started filling up. I now have 0 bytes free.
Edit 1: If I free some space it quickly fills up again.
Edit 2: I noticed that it freed itself by a few KB and then filled up again.

The CPU stays @ 100% usage.

The System Log Viewer says:
```

/var/log/auth.log.0: Error stating file '/var/log/auth.log.0': No such file or directory
/var/log/daemon.log.0: Error stating file '/var/log/daemon.log.0': No such file or directory
/var/log/debug.0: Error stating file '/var/log/debug.0': No such file or directory
/var/log/kern.log.0: Error stating file '/var/log/kern.log.0': No such file or directory
/var/log/messages.0: Error stating file '/var/log/messages.0': No such file or directory
/var/log/user.log.0: Error stating file '/var/log/user.log.0': No such file or directory
/var/log/syslog.0: Error stating file '/var/log/syslog.0': No such file or directory

```
which really gets me thinking. :-/



In /media I see things I didn't see before:
an empty directory called w7
and 3 more files: .directory, .hal-mtab, .hidden
EDIT 3: floppy, cdrom (links) and floppy0 and cdrom0 also appear now and didn't before.

top says
```
12650 george    20   0  970m 908m  10m R 24.6 45.1   0:59.84 gnome-system-lo    
24268 george    20   0  5628 4184 3848 R 23.3  0.2   9:00.70 gvfsd-metadata     
24041 george    20   0  275m 4080 2864 R 14.5  0.2  36:25.19 pulseaudio         
  528 syslog    20   0 34844 1724  836 S 13.1  0.1  27:32.34 rsyslogd           
23450 root      20   0  169m  76m  18m R  8.2  3.8  11:43.81 Xorg               
21384 george    20   0 47748  12m 9.9m R  7.6  0.6   0:03.91 gnome-terminal     
24158 george    20   0 63148  19m  12m S  2.3  1.0   1:12.25 gnome-panel        
32676 george    20   0  179m  87m  24m S  1.6  4.3   0:46.28 opera              
24248 george    20   0 45888  24m 9168 S  1.0  1.2   3:09.49 python             
   26 root      15  -5     0    0    0 S  0.7  0.0   0:14.76 kswapd0            
 1834 root      35  15 11000 9108  772 R  0.7  0.4   1:59.77 preload            
24204 george    20   0 41484  11m 8500 S  0.7  0.5   0:27.71 sensors-applet     
 8580 george    20   0 63512  12m 9.8m S  0.3  0.6   0:00.23 operapluginwrap    
22840 george    20   0  2468 1220  884 R  0.3  0.1   0:00.04 top                
24157 george    20   0  111m  48m  17m R  0.3  2.4   1:57.56 compiz.real        
30819 george    20   0  479m  32m  16m S  0.3  1.6   2:23.04 pidgin             
    1 root      20   0  2640 1452 1048 S  0.0  0.1   0:01.05 init  
```
(btw, how can I see EVERYTHING with top?)

Running programs: Opera 10.10, Pidgin, gDesklets and Evince and until a few moments ago Deluge ran as another user. (I used Switch user to have 2 users logged in)

What is going on, people?

---

### Post by cguy on 2009-11-24
Oh, and two error messages appeared: (same box twice, actually)
```

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
10604000

If you report this situation as a bug, please include:
- The result of xprop -root | grep XKB
- The result of gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd
```


I don't know if this has any relevance to the problem, but the temperature indicator of the HDD shows 0 deg. Bug? Failing sensor? Failing Hdd?
Maybe a restart is due, but I won't restart until I figure out what's with the processes, logs and all. :-?

---

