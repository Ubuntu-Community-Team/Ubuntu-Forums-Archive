---
title: "Last update made my computer lag so much more 2-25-12"
date: 2012-02-27
forum: General Help
---

### Post by Stevens7 on 2012-02-27
If anyone can point me to the files that where included in that update please post them so i can delete them! 

It seems to lag everything from system resources to web-pages.

---

### Post by PaulW2U on 2012-02-27
No one is going to be able to tell you that because not only have you not told us which version/variant of Ubuntu you are using but we don't know how often you update. Less frequent updates result in larger updates.

Do you see the problem after rebooting?

If you run htop or top in a terminal window do you see one or more applications taking more than its fair share of resources?

---

### Post by Stevens7 on 2012-02-27
> **PaulW2U said:**
> No one is going to be able to tell you that because not only have you not told us which version/variant of Ubuntu you are using but we don't know how often you update. Less frequent updates result in larger updates.

Do you see the problem after rebooting?

If you run htop or top in a terminal window do you see one or more applications taking more than its fair share of resources?
I'm running the 11.4 
Yes it's there after re-booting. 
Done!
                                    
 1684 roger     20   0  267m  45m  11m S  1.3  9.8  15:15.47 plugin-containe                            
 3060 roger     20   0 79408  14m  10m S  1.3  3.0   0:02.38 gnome-terminal                             
  879 root      20   0  133m  70m 5764 S  0.7 15.1  19:40.04 Xorg                                       
 1634 roger     20   0  598m 143m  19m S  0.7 30.9  56:05.27 firefox                                    
 1185 roger     20   0  6960 2176  600 S  0.3  0.5   3:33.21 dbus-daemon                                
 1300 roger     20   0  126m 5088 3456 S  0.3  1.1   1:02.34 metacity                                   
 1329 roger     20   0 90388 9244 5388 S  0.3  1.9   0:56.15 unity-2d-panel                             
 3135 roger     20   0  2820 1148  856 R  0.3  0.2   0:00.30 top                                        
    1 root      20   0  3328  772  464 S  0.0  0.2   0:00.80 init                                       
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                   
    3 root      20   0     0    0    0 S  0.0  0.0   0:00.52 ksoftirqd/0                                
    5 root      20   0     0    0    0 S  0.0  0.0   0:00.46 kworker/u:0                                
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset                                     
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper                                    
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns                                      
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.05 sync_supers                                
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                                
   12 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd                                
   13 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd                                    
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ata_sff                                    
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd                                      
   16 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 md                                         
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.23 kworker/u:1                                
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd                                 
   20 root      20   0     0    0    0 S  0.0  0.0   0:06.05 kswapd0                                    
   21 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd                                       
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 fsnotify_mark                              
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                            
   24 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 crypto                                     
   32 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kthrotld

---

### Post by PaulW2U on 2012-02-27
I don't have the answer but my gut feeling is that as plugin-container is related to Firefox and between them they are using 40% of your memory that is where your problem lies. A Google search confirms many other users are having similar problems.

Do you have a lot of Firefox extensions installed?

I'm thinking perhaps you should disable all of your extensions and re-enable them one at a time. May be just one extension is the source of your problems?

---

### Post by Stevens7 on 2012-02-27
I'm trying that now. 
The extentions i have are
Ubuntu Firefox modifications 1.0.2
AvtiveGS 3.5..686
Global Menu bar integration 2.0.2
Quickjava 1.7.5 
united states English spell-checker 5.0.1
adblock plus 2.0.3


My plug-ins are 
Divxwebplayer v.1.4.0.233
Djview 4.7
icedtea-webplugin 1.3.1 (using iced-tea web 1.3.1 (1.1.3-1ubuntu1.1)
Quicktime plug-in 7.6.6
shockwave flash 11.1 r102
VLC multimedia plug in v1.1.12
VLC multimedia plug in (compatible totem 3.0.1)
windows meadia plug in 10 (compatible totem)

---

