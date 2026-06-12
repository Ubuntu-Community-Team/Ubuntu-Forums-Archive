---
title: "Running Ridiculously Slow... What can I do?"
date: 2010-02-01
forum: General Help
---

### Post by lightnb on 2010-02-01
My system (Ubuntu 8.10) has been getting slower and slower and has reached the point where it's become intolerable.

I have a 2.6GHz processor with 4 GB of ram. I've got a nVidia graphics card with 256 mb of it's own ram. So it's not a slow machine by any means.

Yet as I'm typing this sentence, I'm watching Firefox struggle to keep up with me as I type text into this box. I type a sentence and the cursor doesn't move. Then the window greys out while it thinks about the text I've typed. After 10 seconds the window fades back up and the text appears.

When I right click, it takes a full 4 seconds for the context menu to open. My CPU usage is about 20% for both processors. Memory usages is 1.3 GB out of 3.9GB total.

The Google Home Page takes 15 seconds to load. It's almost instantaneous on my other machines. Neither CPU nor the memory usage is spiking.

The problem occurs in two instances of firefox, one with some plug-ins installed, and a second with NO plug-ins installed. 

Switching tabs and scrolling in Nautilus is also slow.

What can I try to fix the problem?

---

### Post by NightwishFan on 2010-02-01
First off, try disabling Compiz Desktop Effects to see if that helps performance, you can do so in System -> Preferences -> Appearence.

Also, open a terminal, and run the command "top" (without quotes). What are the processes using the most amount of CPU?

---

### Post by jamesisin on 2010-02-01
I run into the same typing in the future, reading in the past weirdness (in Opera) from time to time.  I haven't sorted out what is causing it.  I do typically run compiz, though.  Next time it happens I can try disabling it to see if that helps matters.

---

### Post by ManyBeers on 2010-02-01
> **lightnb said:**
> My system (Ubuntu 8.10) has been getting slower and slower and has reached the point where it's become intolerable.

I have a 2.6GHz processor with 4 GB of ram. I've got a nVidia graphics card with 256 mb of it's own ram. So it's not a slow machine by any means.

Yet as I'm typing this sentence, I'm watching Firefox struggle to keep up with me as I type text into this box. I type a sentence and the cursor doesn't move. Then the window greys out while it thinks about the text I've typed. After 10 seconds the window fades back up and the text appears.

When I right click, it takes a full 4 seconds for the context menu to open. My CPU usage is about 20% for both processors. Memory usages is 1.3 GB out of 3.9GB total.

The Google Home Page takes 15 seconds to load. It's almost instantaneous on my other machines. Neither CPU nor the memory usage is spiking.

The problem occurs in two instances of firefox, one with some plug-ins installed, and a second with NO plug-ins installed. 

Switching tabs and scrolling in Nautilus is also slow.

What can I try to fix the problem?

Maybe the harddrive has started to run in PIO mode. This [link]("http://ubuntuforums.org/showthread.php?t=951229&highlight=pio+mode") has a command in it so you can make sure the harddrive is running in DMA.

---

### Post by M1GEO on 2010-02-01
as well as *top*, *htop* is a little more user friendly if you're not used to top.  The program *powertop* may well be useful too.  It can be installed using apt (*sudo apt-get install powertop*), and will tell you what programs/processes/etc are interupting the processor.  I think it may only work for Intel cpus though,

---

### Post by lightnb on 2010-02-01
I've noticed that when running top, Firefox jumps to 100% CPU usage for apparently no reason. Even if I'm not using it...

```
sudo hdparm -i /dev/sda
```

```

/dev/sda:

 Model=Hitachi HTS722012K9SA00                 , FwRev=DCCOC54P, SerialNo=071109DP1C10DJG7PRDP
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=15203kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=234441648
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode
```

---

### Post by M1GEO on 2010-02-01
Maybe try disabling any toolbars, plugins for firefox?  Maybe remove all custom settings from Firefox.  This can be done by "hiding" /home/username/.mozilla/firefox/<random_dir.default>.  Move it, or tar it up, and then see if it works better?

---

### Post by fishbulb1022 on 2010-02-02
You might try clearing your private data in firefox

---

