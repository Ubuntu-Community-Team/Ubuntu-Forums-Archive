---
title: "Ubuntu runs sluggish"
date: 2010-02-12
forum: General Help
---

### Post by Amzo2 on 2010-02-12
Well the title says it all, my ubuntu just seems to run sluggish. I don't have a top end pc, but I think the specs are enough to run it.

Specs:

2.8ghz Processor
512mb of memory.

I'm sure that is enough to run ubuntu. Well anyways, I checked my system monitor, and only about 50% of my ram is in use, and about 20% of my cpu is in use, and that is with my apps like swiftfox, pidgin and torrent client open.

Here is a look at my top

```
Tasks: 144 total,   1 running, 143 sleeping,   0 stopped,   0 zombie
Cpu(s): 12.6%us,  3.3%sy,  0.0%ni, 80.1%id,  3.0%wa,  0.7%hi,  0.3%si,  0.0%st
Mem:    509292k total,   493112k used,    16180k free,    20800k buffers
Swap:  1494004k total,   168264k used,  1325740k free,   191284k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                         
12970 amzo      20   0 58580 7708 4480 S  3.3  1.5   0:15.24 gnome-terminal                                                  
 2092 amzo      20   0 97924  19m 6728 S  2.7  4.0   0:20.64 deluge                                                          
12321 root      20   0 74508  25m 5940 S  2.7  5.1  20:31.69 Xorg                                                            
14679 amzo      20   0  150m  22m 9148 S  1.7  4.6   5:28.57 pidgin                                                          
26769 amzo      20   0  140m  10m 3420 S  1.7  2.1  23:35.19 vidalia                                                         
 2127 amzo      20   0 83132  21m 3764 S  1.0  4.3   0:36.56 deluged                                                         
26278 amzo      20   0  548m 101m  17m S  1.0 20.4 295:34.99 swiftfox-bin                                                    
12658 amzo      20   0 55988 3308 2700 S  0.7  0.6   4:24.15 ica                                                             
12588 amzo      20   0 47580  11m 6020 S  0.3  2.3   1:43.88 gnome-panel                                                     
12592 amzo      20   0  102m 9.9m 4540 S  0.3  2.0   0:10.37 nautilus                                                        
    1 root      20   0  2632  808  540 S  0.0  0.2   0:01.14 init                                                            
    2 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kthreadd                                                        
    3 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 migration/0                                                     
    4 root      15  -5     0    0    0 S  0.0  0.0   0:00.59 ksoftirqd/0                                                     
    5 root      RT  -5     0    0    0 S  0.0  0.0   0:00.00 watchdog/0                                                      
    6 root      15  -5     0    0    0 S  0.0  0.0   0:01.26 events/0                                                        
    7 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 cpuset                                                          
    8 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khelper                                                         
    9 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 netns                                                           
   10 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 async/mgr                                                       
   11 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kintegrityd/0                                                   
   12 root      15  -5     0    0    0 S  0.0  0.0   0:00.55 kblockd/0                                                       
   13 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid                                                          
   14 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify                                                    
   15 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_hotplug                                                   
   16 root      15  -5     0    0    0 S  0.0  0.0   0:31.80 ata/0                                                           
   17 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ata_aux                                                         
   18 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ksuspend_usbd                                                   
   19 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 khubd                                                           
   20 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod                                                         
   21 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 kmmcd                                                           
   22 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 bluetooth                                                       
   23 root      20   0     0    0    0 S  0.0  0.0   0:00.00 khungtaskd                                                      
   26 root      15  -5     0    0    0 S  0.0  0.0   0:08.19 kswapd0                                                         
   27 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0                                                           
   28 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 ecryptfs-kthrea                                                 
   29 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 crypto/0                                                        
   33 root      15  -5     0    0    0 S  0.0  0.0   0:00.00 scsi_eh_0  
```

And here is a look at my disk read / write speeds

```
/dev/sda1:
 Timing cached reads:   1122 MB in  2.00 seconds = 560.71 MB/sec
 Timing buffered disk reads:  136 MB in  3.07 seconds =  44.37 MB/sec

```

---

### Post by iponeverything on 2010-02-12
what is video hardware. There has been some issues with ATI -- I also problem with the Intel hardware on a lenovo with 9.10 before installing the updates.

---

### Post by Amzo2 on 2010-02-12
I am using an nvidia geforce fx 5200, and have the drivers installed. 173 legacy drivers

---

### Post by cronos on 2010-02-12
It is probably the video card.  I had a nvidia 7950GT, and Ubuntu ran nice and fast.  But, unfortunately my card broke, and now I am using my old GeForce FX 5200 card.  Everything runs slow now... And, sadly my Windows XP is faster than Ubuntu. :(

---

### Post by Amzo2 on 2010-02-12
Ahh, I will update my card, not sure what card to get though, wouldn't want a state of the art one, and I'm not really too good with hardware.

---

### Post by robertcoulson on 2010-02-12
Well..I use the  nvidia geforce fx 5200 and both XP and Ubuntu run very fast on my sort of older machine, unless there is a problem with the card itself.
Bob

---

### Post by cronos on 2010-02-12
Interesting... So, you can watch movies without any issues?  What version driver are you using?  My Nvidia driver version is 96.43.13, which seems quite old.

---

### Post by robertcoulson on 2010-02-12
I believe it is 173...???
Bob

---

### Post by cronos on 2010-02-13
Thanks. I just upgraded the driver to 173.14.20 , and my computer seems to be more responsive, and can watch movies again, etc.

Hopefully Amzo2 will have success, too.  My PC is similar; AMD 3000+ with 1GB ram.

---

### Post by Amzo2 on 2010-02-13
Yeah, I have the latest drivers, and I have the desktop effects disabled, might just be my memory, because it's slow memory. But, I might give XFCE a try and see if there is any improvement.

---

