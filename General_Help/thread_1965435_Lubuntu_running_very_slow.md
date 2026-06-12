---
title: "Lubuntu running very slow"
date: 2012-04-25
forum: General Help
---

### Post by Blank000 on 2012-04-25
Hello everyone
A couple of days ago i installed my first linux - Xubuntu. But it was running so slow that it was practically useless. Zvacet suggested i try Lubuntu. But, things are the same (i did a new, clean install).

PC is Pentium IV 1.8GHz, with 512mb RAM and judging by what i read it should run smoothly. But it doesn't. Everything is a wait. Open new tab in Midori - wait. Alt+Tab to switch - wait. Right click on desktop for menu - wait. Didn't even try to install GIMP, i guess it would be completely useless, just like it was in Xubuntu (note: GIMP runs normally on same PC under XP). Everything is slowed down, and barely usable. Even though i reduced swappiness and it doesn't touch swap.


Mastablasta suggested it could be graphics card support issue, he asked for some information (read about it here [http://ubuntuforums.org/showthread.php?t=1961652](http://ubuntuforums.org/showthread.php?t=1961652)), so here they are for Lubuntu, if it helps.

**lspci**
```
lubuntu@lubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845 845 [Brookdale] Chipset Host Bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 82845 845 [Brookdale] Chipset AGP Bridge (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 12)
00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 12)
00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 Controller (rev 12)
00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus Controller (rev 12)
00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB Controller #1 (rev 12)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:02.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 43)
02:03.0 Communication controller: Ambient Technologies Inc HaM controllerless modem (rev 02)
02:06.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
02:07.0 Multimedia audio controller: C-Media Electronics Inc CM8738 (rev 10)
lubuntu@lubuntu:~$ 
```


**top**
```
ubuntu@lubuntu:~$ top

top - 23:38:08 up  1:10,  0 users,  load average: 0.06, 0.15, 0.30
Tasks:  97 total,   1 running,  95 sleeping,   0 stopped,   1 zombie
Cpu(s):  8.3%us,  1.7%sy,  0.0%ni, 90.1%id,  0.0%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:    508344k total,   487284k used,    21060k free,    18596k buffers
Swap:   524284k total,    55400k used,   468884k free,   187460k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                          
 1544 lubuntu   20   0  606m 230m  42m S  7.9 46.5  15:45.67 midori                                                                                           
 1023 root      20   0 45184  16m 6592 S  2.6  3.3  13:10.47 Xorg                                                                                             
 2606 lubuntu   20   0  154m  11m 8140 S  1.0  2.3   0:01.35 lxterminal                                                                                       
 1161 lubuntu   20   0  5216 1580 1388 S  0.3  0.3   0:01.50 xscreensaver                                                                                     
 2661 lubuntu   20   0  2808 1124  856 R  0.3  0.2   0:00.11 top                                                                                              
    1 root      20   0  3324 1608 1224 S  0.0  0.3   0:01.21 init                                                                                             
    2 root      20   0     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                                                         
    3 root      20   0     0    0    0 S  0.0  0.0   0:01.84 ksoftirqd/0                                                                                      
    5 root      20   0     0    0    0 S  0.0  0.0   0:00.70 kworker/u:0                                                                                      
    6 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                                                      
    7 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 cpuset                                                                                           
    8 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 khelper                                                                                          
    9 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 netns                                                                                            
   10 root      20   0     0    0    0 S  0.0  0.0   0:00.02 sync_supers                                                                                      
   11 root      20   0     0    0    0 S  0.0  0.0   0:00.00 bdi-default                                                                                      
   12 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kintegrityd                                                                                      
   13 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kblockd                                                                                          
   14 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ata_sff                                                                                          
   15 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khubd                                                                                            
   16 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 md                                                                                               
   17 root      20   0     0    0    0 S  0.0  0.0   0:00.22 kworker/u:1                                                                                      
   19 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd                                                                                       
   20 root      20   0     0    0    0 S  0.0  0.0   0:00.64 kswapd0                                                                                          
   21 root      25   5     0    0    0 S  0.0  0.0   0:00.00 ksmd                                                                                             
   22 root      20   0     0    0    0 S  0.0  0.0   0:00.00 fsnotify_mark                                                                                    
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                                                                                  
   24 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 crypto                                                                                           
   32 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 kthrotld                                                                                         
   34 root      20   0     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0                                                                                        
   35 root      20   0     0    0    0 S  0.0  0.0   0:00.68 scsi_eh_1                                                                                        
  191 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 firewire                                                                                         
  220 root      20   0     0    0    0 S  0.0  0.0   0:00.50 jbd2/sda2-8                                                                                      
  221 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ext4-dio-unwrit                                                                                  
  276 root      20   0  2648  524  448 S  0.0  0.1   0:00.43 upstart-udev-br                                                                                  
  279 root      20   0  3076  904  712 S  0.0  0.2   0:00.30 udevd                                                                                            
  404 syslog    20   0 27908  936  936 S  0.0  0.2   0:00.72 rsyslogd                                                                                         
  423 messageb  20   0  3936 1484 1096 S  0.0  0.3   0:01.45 dbus-daemon                                                                                      
  446 root      20   0  6864 2100 1936 S  0.0  0.4   0:00.35 modem-manager                                                                                    
  450 avahi     20   0  3316 1308 1216 S  0.0  0.3   0:00.07 avahi-daemon                                                                                     
  453 avahi     20   0  3316  228  216 S  0.0  0.0   0:00.00 avahi-daemon                                                                                     
  475 root      20   0  3072  536  328 S  0.0  0.1   0:00.00 udevd                                                                                            
  476 root      20   0 26728 3592 3296 S  0.0  0.7   0:00.19 NetworkManager                                                                                   
  479 root      20   0  3072  420  292 S  0.0  0.1   0:00.00 udevd                                                                                            
  490 root      20   0 23468 2988 2744 S  0.0  0.6   0:00.50 polkitd                                                                                          
  532 root      20   0  2736  592  592 S  0.0  0.1   0:00.01 dhclient                                                                                         
  596 root       0 -20     0    0    0 S  0.0  0.0   0:00.00 ttm_swap                                                                                         
  768 root      20   0  2652  288  204 S  0.0  0.1   0:00.04 upstart-socket-                                                                                  
  866 root      20   0     0    0    0 S  0.0  0.0   0:00.33 flush-8:0                                                                                        
  872 root      20   0  1968  468  468 S  0.0  0.1   0:00.00 getty
```

**free -m**
```
lubuntu@lubuntu:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           496        477         18          0         18        183
-/+ buffers/cache:        275        220
Swap:          511         53        458
lubuntu@lubuntu:~$ 
```


Is there anything i can do to make it perform at least as XP, if not faster?

Thanks in advance!

---

### Post by holycow131415 on 2012-04-25
the free command is displaying 496mb instead of 512. Seems to me your ram is dying out. Your harddrive also may be the cause of it being slow too. A good size for swap is normally 2x your ram too.

RAM is cheap, id suggest upgrading it to 1gb.

You could download the minimum ubuntu CD and install openbox or lxde.

---

### Post by QIII on 2012-04-25
In my experience, Midori is dog slow.  And it certainly should not be consuming that much memory.

If you have Midori running when you are trying to do other things, that might be part of your problem.  Midori should be consuming maybe 50M.

You could try Iceweasel.  I use it on low spec systems.  I even use it with Bodhi, even though Midori is the default.

Have you done a memtest recently?

---

### Post by Blank000 on 2012-04-25
> **QIII said:**
> In my experience, Midori is dog slow.  And it certainly should not be consuming that much memory.

I installed Midori because default Chromium wasn't usable, even for "normal" pages. Not to mention anything heavier, it couldn't play youtube video without twitching it. At least Midori works.


> Have you done a memtest recently?

No, didn't have the need for it. Under XP everything runs as it always did.

---

### Post by claracc on 2012-04-26
I recommend epiphany browser instead of midori.

For my lubuntu 11.04 pentium III with 512 MB ram, epiphany browser is more responsive although sometimes I have weird crashes.

---

### Post by mastablasta on 2012-04-26
> **Blank000 said:**
>  
No, didn't have the need for it. Under XP everything runs as it always did.
 
 
memorry is used in a different way in windows that in linux. the systems don't load it in same way. so any errors will pop out first in linux.
 
ram could also be taken by graphics chip. also some chips have poor linux support. yours might be one of them. which would aslo explain why windows works better.
 
if that is the case what you could do is try to upgrade the drivers via edgers PPA. 
 
ATI dropped support for your card so drivers had to be reverse engineer by community to make them work. soemtimes it's a job well done, but sometiems it's bad. it works but not really as good as it should. it's AMD's fault as (besides dropping linux support) they also didn't release the specs to help the community create the drivers.

---

### Post by marinara on 2012-04-26
your hardware is failing.  no idea what though

---

