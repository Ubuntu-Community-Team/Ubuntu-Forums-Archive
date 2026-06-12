---
title: "Why is my desktop so heavy??"
date: 2010-03-13
forum: General Help
---

### Post by Jheric on 2010-03-13
Yesterday, I installed openbox and pcman on my old desktop and was able take the desktop ram load from 275mb to 120mb. (openbox, pcman, kupfer, gnome-panel)

I was so pleased with the increased headroom and performance that I wanted to do it on my macbook. Usually my macbook has as desktop ram load of about 350mb... which I find excessive as that is heavier than OS X. That's running gnome, nautilus, compiz, and gnome-do at startup.

I performed a similar procedure today to create the same setup on my laptop and... strangely, my ram usage on the desktop is still close to 300mb! 

I've brought up system monitor and added up the ram of all the processes it detected myself and it only added up to about 50mb. How is it that my desktop is still so heavy in a minimal environment??

(both machines are Karmic 9.10, by the way. The desktop is hardwired to the internet while my laptop uses Wicd)

---

### Post by Jheric on 2010-03-13
Yeah, I just logged into a fresh instance of my gnome/compiz session after restarting... it's 320mb ram. How could I only have gained 20mb switching to openbox?

I also tried LXDE earlier, with similar results. How can I track down whatever eating up all my ram?

Here's my top (most of it anywho). Anything out of the ordinary?

```

 PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                       
 3662 justalea  40   0  350m  38m  18m S    0  2.2   0:01.78 /usr/share/kupf               
 3489 root      40   0  361m  26m  12m S    1  1.5   0:17.80 Xorg                           3655 justalea  40   0  419m  24m  15m S    0  1.4   0:01.28 gnome-panel                   
 3652 justalea  40   0  371m  17m  11m S    0  1.0   0:00.69 pcmanfm                        3757 justalea  40   0  314m  17m  11m S    1  1.0   0:00.78 gnome-terminal                
 3857 justalea  40   0  305m  10m 7560 S    0  0.6   0:00.21 gnome-settings-                1593 root      40   0 73904 9356 2112 S    1  0.5   0:03.05 wicd                          
 1641 root      40   0 63820 8620 3168 S    0  0.5   0:01.03 wicd-monitor                   3862 justalea  40   0  162m 7372 5700 S    0  0.4   0:00.03 notify-osd                    
 3603 justalea  40   0 97816 7076 4916 S    0  0.4   0:00.17 openbox                        3659 justalea  40   0 46300 6112 2320 S    0  0.3   0:00.09 gconfd-2                      
 3693 justalea  20   0  261m 5076 3572 S    0  0.3   0:00.13 pulseaudio                     1795 mpd       40   0  207m 4964  964 S    0  0.3   0:00.01 mpd                           
  701 haldaemo  40   0 34004 4560 3600 S    0  0.3   0:00.20 hald                           3759 justalea  40   0 21500 4272 1588 S    0  0.2   0:00.11 bash                          
 3681 justalea  40   0  140m 3984 2916 S    0  0.2   0:00.05 bonobo-activati                2174 root      40   0 53700 3892 2888 S    0  0.2   0:00.03 polkitd                       
 3488 root      40   0 76848 3876 3048 S    0  0.2   0:00.03 gdm-simple-slav                1955 root      40   0 47964 3824 2268 S    0  0.2   0:00.06 devkit-power-da               
 1229 root      40   0 74924 3744 2964 S    0  0.2   0:00.04 gdm-binary                     3951 justalea  40   0 98752 3720 2500 S    0  0.2   0:02.91 conky                         
 3553 root      40   0 89288 3396 2660 S    0  0.2   0:00.04 gdm-session-wor                3699 justalea  20   0 94308 3384 2632 S    0  0.2   0:00.01 gconf-helper                  
 1562 root      40   0 94112 3320 2356 S    0  0.2   0:00.01 smbd                            814 root      40   0  115m 3240 2208 S    0  0.2   0:00.04 console-kit-dae               
 3674 justalea  40   0 54128 3156 2536 S    0  0.2   0:00.02 gvfs-gdu-volume               
 2123 root      40   0 42452 3048 2376 S    0  0.2   0:00.25 devkit-disks-da               
 3702 justalea  40   0 49692 2976 2468 S    0  0.2   0:00.00 gvfsd-trash                   
 3651 justalea  40   0 30228 2944 1056 S    0  0.2   0:00.21 xcompmgr                      
 3588 justalea  40   0 88472 2904 2152 S    0  0.2   0:00.01 gnome-keyring-d               
 1675 root      40   0 75156 2840 2068 S    0  0.2   0:00.02 cupsd                         
 3669 justalea  40   0 75492 2788 2092 S    0  0.2   0:00.00 gvfs-fuse-daemo               
 3676 justalea  40   0 50504 2504 1960 S    0  0.1   0:00.00 gvfs-gphoto2-vo               


```

---

