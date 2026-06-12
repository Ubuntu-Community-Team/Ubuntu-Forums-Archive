---
title: "RAM and SWAP question..."
date: 2010-01-01
forum: General Help
---

### Post by sagitta on 2010-01-01
1st things first, My system Specs:
Pentium D 2.66GHZ
1GB RAM
Intel 945G graphics chipset
x2 80GB SATA HD's
Ultimate Edition 2.3 Gamers(Ubuntu 9.04 with 2.26.32 Kernel)

If I could then I would have already migrated to 9.10 but the silly tandem of my monitor and graphics card prevents me from doing so. The upgrade to 9.10 button looks tempting but I'll pass on to it due to the ill feeling Im getting every time update manager reminds me of it so I settled with just using the latest linux kernels...  AND IT WORKS MARVELOUSLY!

On to my problem, my system seems to fear using physical RAM and seems to like stuffing my SWAP with everything! Take a look at this screenshot:
[[img]http://i191.photobucket.com/albums/z48/sagittamagica/th_RAMSWAP.png[/img]]("http://i191.photobucket.com/albums/z48/sagittamagica/RAMSWAP.png")

By this time, system performance was already awful..

All I was doing was some encoding with mencoder; the above shot was taken AFTER the encoding finished. And around 5 webpages on Google Chrome..
My system swapiness has already been set to 10

Why is it that my swap is being consumed first with my Physical RAM is left untouched?  Is there anyway to make my system eat RAM first before starting swapping?

Thanks!

---

### Post by User0123 on 2010-01-01
Change your swappiness

---

### Post by ibuclaw on 2010-01-01
Hmm... what you should really be asking is "What is consuming that much memory?"

What is the output of
```
top -n1
```

And what happens when you run the following in order:
```

sudo sync
sudo bash -c 'echo 3 > /proc/sys/vm/drop_caches'

```

Regards
Iain

---

### Post by sagitta on 2010-01-01
I had already restarted my PC and set swappiness to 0, it was crawling pretty bad already..

anyways, here's my top -nl
```
top - 22:28:12 up  1:24,  5 users,  load average: 1.14, 0.95, 0.70
Tasks: 168 total,   3 running, 165 sleeping,   0 stopped,   0 zombie
Cpu(s): 45.8%us,  4.9%sy,  0.7%ni, 45.5%id,  2.9%wa,  0.1%hi,  0.2%si,  0.0%st
Mem:   1016964k total,  1000432k used,    16532k free,    10564k buffers
Swap:        0k total,        0k used,        0k free,   555940k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
13472 sagittax  40   0 59120  31m  11m R   92  3.2   5:55.86 mencoder           
13468 sagittax  40   0 77400  35m 7784 S   25  3.5   2:01.65 mplayer            
 4305 sagittax  20   0  228m  69m  23m S    8  7.0   5:41.18 chromium-browse    
 3348 root      40   0 83012  18m 9576 S    4  1.8   3:30.59 Xorg               
 4063 sagittax  40   0 85568  23m  14m S    4  2.4   0:25.65 nautilus           
 4061 sagittax  40   0  173m  24m 5948 S    2  2.5   1:20.50 compiz.real        
 4072 sagittax  40   0  7240 2676 2084 S    2  0.3   0:01.76 cdemud             
 4228 sagittax  40   0 70672  10m 3868 S    2  1.0   0:15.76 deluged            
11622 sagittax  21   1  112m  27m 9864 S    2  2.8   0:07.31 chromium-browse    
13473 sagittax  40   0 38012 9664 8496 S    2  1.0   0:08.13 mencoder           
14278 sagittax  40   0  2444 1108  828 R    2  0.1   0:00.01 top                
    1 root      40   0  3084 1808  484 S    0  0.2   0:00.99 init               
    2 root      40   0     0    0    0 S    0  0.0   0:00.00 kthreadd           
    3 root      RT   0     0    0    0 S    0  0.0   0:00.01 migration/0        
    4 root      20   0     0    0    0 S    0  0.0   0:00.34 ksoftirqd/0        
    5 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0         
    6 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/1
```

Currently encoding something mencoder..
As for the 2 commands you gave me.. Nothing changed, atleast as far as I can see :D

---

### Post by mkalbere on 2010-01-20
swap is set to 0k, meaning you have no swap partition mounted.
Try

swapon -a   to enable all your swap partition, if it doesn't work google to create&enable a swap part

---

