---
title: "High iowait on 10.04 lamp"
date: 2011-10-17
forum: General Help
---

### Post by nowave7 on 2011-10-17
Hey all,

I'm experiencing pretty high iowaits while running a developer lamp and eclipse on 10.04. The culprits are, judging by iotop, eclipse and apache2, but mostly eclipse, doing it's DLTK indexing, SVN cache update, and what not. Not sure if this is the right place to be asking the question(it may be better to ask eclipse or apache guys), but are there any general pointers as to how to reduce these high iowaits? These high iowaits also occur while indexing large number of files, for example, updating my pictures library, or some background processes like beam.smp and locate.updatedb. The filesystem is ext4, and I have 3GB of memory.

---

### Post by blueridgedog on 2011-10-17
Some general suggestions:
-put operations on different physical disks to increase IO performance
-put in more memory and install the 64 bit OS so that you can cache more and swap less.  Swap and high iowait create a death spiral (you get the picture).
-schedule your IO intensive tasks well apart from each other

---

### Post by nowave7 on 2011-10-18
Hey blueridgedog,

Thanks for the reply, but I'm afraid that these pointers, though make sense, are not going to help me, since this is my work machine and I'm afraid I won't be getting a new disk or some more memory. :( Installing 64 bit OS is a good tip, but I can't afford myself to spend a whole day installing a new OS. Are there any more specific pointers then? I've tried setting the noatime option in fstab, but that does not seem to do the trick. Anything I can do with hdparm maybe?

---

### Post by nowave7 on 2011-10-18
Just to throw in some numbers:

```
hdparm -tT /dev/sda 

/dev/sda:
 Timing cached reads:   1906 MB in  2.00 seconds = 952.84 MB/sec
 Timing buffered disk reads:  328 MB in  3.01 seconds = 108.98 MB/sec


hdparm  /dev/sda 

/dev/sda:
 multcount     = 16 (on)
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 60801/255/63, sectors = 976773168, start = 0


hdparm -i /dev/sda 

/dev/sda:

 Model=ST3500320AS, FwRev=SD15, SerialNo=5QM1PTXH
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs RotSpdTol>.5% }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=unknown, BuffSize=0kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=976773168
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=no WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-4,5,6,7

 * signifies the current active mode



```

---

### Post by blueridgedog on 2011-10-18
During these times, are you swapping?  If you can eliminate swap usage, you can probably improve things.  Are there processes you can eliminate?

---

### Post by nowave7 on 2011-10-19
Well, not that many processes that can be eliminated. As I said this is a developer machine, and I need a lot of programs/processes running at the same time: Apache web server, eclipse, mail server, mail client, couple of web browsers, few terminal windows, not to mention things like instant messaging programs, music player, file browsers...
I don't have CONFIG_TASK_DELAY_ACCT enabled in the kernel, since I'm using Ubuntu stock kernel, so SWAPIN and IO are unavailable.

---

### Post by nowave7 on 2011-10-19
I was looking at iotop output while Eclipse was doing it's DLTK indexing and other initializations, DISK READ was at times 15MB/s and over. Don't know if this is normal, but seems pretty high.

---

### Post by blueridgedog on 2011-10-19
When your IO wait gets high...what is the output of "free"?

---

### Post by nowave7 on 2011-10-19
These are the values of free with high iowait:
```
             total       used       free     shared    buffers     cached
Mem:       3225660    3136360      89300          0     181748     935380
-/+ buffers/cache:    2019232    1206428
Swap:      9449464      93920    9355544


```

---

### Post by blueridgedog on 2011-10-19
As suspected, you are swapping and having disk intensive IO, which then grinds to a halt.  

A good read, but one that might not help much is:

[http://www.linuxjournal.com/magazine/hack-and-linux-troubleshooting-part-i-high-load?page=0,0](http://www.linuxjournal.com/magazine/hack-and-linux-troubleshooting-part-i-high-load?page=0,0)

You ultimately need more ram or to reduce programs in memory while working with your development tools (browsers are real memory hogs).  If you can stop swapping while working, I think your IO wait will go down.

---

### Post by nowave7 on 2011-10-19
Ah ok... Makes sense. Well, thanks for the help. I'll give this article a look, maybe it shed's more light on the matter.

---

### Post by blueridgedog on 2011-10-19
An alternative would be to try another desktop environment for your development rig.  FVWM or similar would get a smaller RAM footprint that may solve your issues.  

Another good read:
[https://help.ubuntu.com/community/FVWM](https://help.ubuntu.com/community/FVWM)
and
[https://help.ubuntu.com/community/FVWM-Crystal](https://help.ubuntu.com/community/FVWM-Crystal)

---

### Post by nowave7 on 2011-10-19
Thank you for the tip, I'll most definitely give it a go! :)

---

