---
title: "Slow boot after login lately"
date: 2012-04-15
forum: General Help
---

### Post by PCFreak2 on 2012-04-15
After I login, for the past week or so, my computer has been loading the desktop pretty slowly

Ubuntu x32 11.04

Specs of PC:

[http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=65267&tmp_task=prodinfoCategory&cc=us&dlc=en&lang=en&lc=en&product=4107708](http://h10025.www1.hp.com/ewfrf/wc/documentSubCategory?tmp_rule=65267&tmp_task=prodinfoCategory&cc=us&dlc=en&lang=en&lc=en&product=4107708)

---

### Post by abyrne on 2012-04-15
Have you installed any new programs or updates recently?

---

### Post by PCFreak2 on 2012-04-15
Yes

---

### Post by abyrne on 2012-04-15
What specifically have you installed?

---

### Post by PCFreak2 on 2012-04-15
Updates, the new kernel
Urban Terror

---

### Post by abyrne on 2012-04-15
It could possibly have something to do with the kernel update. Try rebooting and holding down the shift key while starting up again, which should bring up the GRUB menu. Use the arrow keys to select "Previous Linux Versions" and press enter. Then select the first non-recovery kernel listed, press enter one more time, and see if your boot times improve.

---

### Post by PCFreak2 on 2012-04-15
I already tried it
I don't think it was any faster

---

### Post by abyrne on 2012-04-15
Ok, immediately after entering your password in the login screen and hitting enter, switch to TTY1 by pressing Ctrl-Alt-F1, login using your normal credentials, and run the command
```
top
```
and post the top 5 programs on the list.
You can return to the desktop by pressing Ctrl-Alt-F7

---

### Post by PCFreak2 on 2012-04-15
Shouldn't I run top before I type my password??

---

### Post by abyrne on 2012-04-15
> Shouldn't I run top before I type my password??
In retrospect, that's probably a better way to do it. Go for it.

---

### Post by PCFreak2 on 2012-04-15
Ok
I will try it
But I'm redownloading Urban Terror right now
So I can't reboot

You can help me with my Urban Terror problems  ;)

[http://ubuntuforums.org/showthread.php?t=1933167](http://ubuntuforums.org/showthread.php?t=1933167)

---

### Post by PCFreak2 on 2012-04-15
```
1777 pcfreak2  20   0 36784  21m 8580 D   14  0.8   0:00.42 ubuntuone-launc                                                                                             
 1221 root      20   0  118m  44m  12m S    5  1.6   0:02.27 Xorg                                                                                                        
 1778 pcfreak2  20   0 35104  16m 9324 S    5  0.6   0:00.14 applet.py                                                                                                   
 1445 pcfreak2  20   0  141m  35m  13m S    1  1.3   0:00.49 compiz                                                                                                      
 1467 root      20   0 23356 3540 2788 S    1  0.1   0:00.07 udisks-daemon                                                                                               
 1713 pcfreak2  20   0 94348  13m  10m S    1  0.5   0:00.22 gnome-terminal                                                                                              
 1492 pcfreak2  20   0  133m  36m  19m S    1  1.3   0:02.05 docky                                                                                                       
 1380 pcfreak2  20   0 36356 7204 5736 S    0  0.3   0:00.11 gnome-session                                                                                               
 1430 pcfreak2  20   0 98.8m  11m 8900 S    0  0.4   0:00.22 gnome-settings-                                                                                             
    1 root      20   0  2916 1784 1248 S    0  0.1   0:00.40 init                                                                                                        
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                                    
    3 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/0                                                                                                 
    4 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/0:0                                                                                                 
    5 root      20   0     0    0    0 S    0  0.0   0:00.25 kworker/u:0                                                                                                 
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/0                                                                                                 
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1                                                                                                 
    8 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:0                                                                                                 
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 ksoftirqd/1                                                                                                 
   10 root      20   0     0    0    0 R    0  0.0   0:00.02 kworker/0:1                                                                                                 
   11 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                                      
   12 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                                     
   13 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                                                       
   14 root      20   0     0    0    0 S    0  0.0   0:00.27 kworker/u:1                                                                                                 
   15 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                                                                                                 
   16 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                                                 
   17 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd                                                                                                 
   18 root       0 -20     0    0    0 S    0  0.0   0:00.00 kblockd                                                                                                     
   19 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpid                                                                                                      
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_notify                                                                                                
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 kacpi_hotplug                                                                                               
   22 root       0 -20     0    0    0 S    0  0.0   0:00.00 ata_sff                                                                                                     
   23 root      20   0     0    0    0 S    0  0.0   0:00.00 khubd                                                                                                       
   24 root       0 -20     0    0    0 S    0  0.0   0:00.00 md                                                                                                          
   25 root      20   0     0    0    0 S    0  0.0   0:00.07 kworker/1:1        
```

---

### Post by PCFreak2 on 2012-04-16
Bump?
I really want this to be fixed
Any help please??

---

### Post by PCFreak2 on 2012-04-18
I guess I'm switching back to Debian

---

### Post by PCFreak2 on 2012-04-26
Any help??

---

