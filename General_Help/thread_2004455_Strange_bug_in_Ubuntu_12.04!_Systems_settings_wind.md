---
title: "Strange bug in Ubuntu 12.04! Systems settings window won't shut, and keeps popping up"
date: 2012-06-15
forum: General Help
---

### Post by clp32r on 2012-06-15
Hi,

I've got a really strange bug with ubuntu 12.04, using unity. I can't use any of the applications in the systems settings menu (e.g. sound, backup, etc). When I try to, instead the systems settings window pops up. Then when I try and shut it, it pops back up. It even pops back up on top of what ever else I am doing like this browser window.
Switching the computer on and off doesn't fix it. As soon as the window pops up, it starts to work the processors, and the fan stays on. Here is a top:

9301 rsmith    20   0     0    0    0 D   11  0.0   0:00.34 gnome-control-c    
 1050 root      20   0 77684  32m 7828 S    7  0.8   0:30.10 Xorg               
 2286 rsmith    20   0  372m  94m  31m S    7  2.4   0:42.78 firefox            
 9307 rsmith    20   0 41024   9m 8136 R    6  0.3   0:00.17 gnome-control-c    
 1835 rsmith    20   0  264m  68m  32m S    5  1.8   0:20.66 compiz             
 2085 rsmith    20   0  162m  21m  15m S    4  0.6   0:17.52 gnome-control-c    
 1808 rsmith    20   0  6048 2600  616 S    2  0.1   0:07.55 dbus-daemon        
 8742 rsmith    20   0 92624  14m  10m S    2  0.4   0:00.46 gnome-terminal     
 1816 rsmith    20   0  143m  15m  11m S    1  0.4   0:02.00 gnome-settings-    
    1 root      20   0  3640 1984 1284 S    0  0.0   0:01.43 init               
   81 root      20   0     0    0    0 S    0  0.0   0:00.57 kworker/0:2        
 1726 rsmith    20   0 54316 3212 2688 S    0  0.1   0:00.36 gnome-keyring-d    
 1844 rsmith    20   0  157m  26m  16m S    0  0.7   0:02.58 nautilus           
 1912 rsmith    20   0 41412   9m 8000 S    0  0.3   0:00.89 gtk-window-deco    
 1942 rsmith    20   0  124m 5960 4824 S    0  0.2   0:01.50 indicator-sound    
 2012 rsmith    20   0 76000 9804 7244 S    0  0.2   0:01.22 unity-applicati    
 2014 rsmith    20   0 89288 5668 4692 S    0  0.1   0:00.97 unity-files-dae   

Please help! I can't back up my system. And if it wasn't Ubuntu, I'd think this was a virus. What's going on?!?

Thanks!

Just to add something - the process that is making all the cpu usage is constantly changing its pid. So it's not a single process, but a new process that keeps happening again and again.....

To add something else, it seems to be something to do with gnome-control-c. When ever I try to kill the process using CPU, it changes PID. and there's always some defunct processes around, but also changin PID (zombies???). I tried killing the parent process using a: kill -9
The systems settings window popped back up! This is fun....

NEW INFO: This problem seems to have been related to Python somehow. It went away when I changed the symbolic link from python 3.2 to 2.7:

sudo ln -s /usr/bin/python2.7 /usr/bin/python
sudo vi /usr/share/python/debian_defaults
....and changed the line 'default version' so as is was 2.7 too...
default-version = python2.7

---

### Post by aunderwood on 2012-07-31
I too started experiencing this issue. Not sure what caused it as I've made no system change. It appears to happen when I right click on the desktop and select change my background. 

Perhaps the packages for personalisation are broken?

---

### Post by clappboard on 2012-07-31
If you believe this is a bug, please report it to launchpad by running the command:
```
ubuntu-bug gnome-control-center
```
Please also remember to check and make sure that the bug is not already reported.  Duplicate bugs are running rampant on launchpad, so always make a cursory check of the known bugs part of your bug-reporting process.
Your help will always be appreciated by the devs there :)

---

