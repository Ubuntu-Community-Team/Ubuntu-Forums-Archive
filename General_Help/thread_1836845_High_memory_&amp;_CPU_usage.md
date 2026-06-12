---
title: "High memory &amp; CPU usage"
date: 2011-08-31
forum: General Help
---

### Post by PHPspirit on 2011-08-31
Hi there fellow Ubuntu users!

First of all I'd like to say that I'll try to explain my problem as best as I can because I'm not native English speaker, I'm from Slovakia, so keep that in mind. Anyways, let's try solve to my problem;

I was using Win XP until yesterday when I decided to try Ubuntu 11.04. I downloaded and installed it from my USB. First thing I noticed was that everything is sooo slow and laggy. So I thought I need to upgrade linux & drivers so I did that. I restarted my PC and nothing changed. Then, I googled 'ubuntu 11.04 is slow' and I found a lot of people were complaining about speed of 11.04. So I downloaded Ubuntu 10.04 [lucid lynx] and I thought everything is gonna be alright. Wrong. After installing 10.04 I couldn't change even simplest things like screen resolution (only two options were available: 640x480 and 800x600]. Then, I found this command on the internet "gedit /etc/X11/xorg.conf" and I also found out that my xorg.conf is empty. Is that ok? I added these lines, then:
Section "Device"
Identifier "Configured Video Device"
Option "PanelSize" "1024x768"
Option "sw_cursor"
EndSection

And after rebooting my system, I could switch to 1024x768 and even higher. I don't know if helped rebooting my system or adding those lines to xorg.conf but it doesn't matter for now. But one problem is giving me a headache: Why the heck is my linux eating so much CPU and Memory.
CPU usage is bouncing between 30 and 90% but 60% mostly.
RAM usage is 65% and higher, it almost never goes below that.
Also everything is so laggy. When I'm watching a flash video, my mouse flashes when I'm moving with it and also when I'm moving with linux windows, it looks like graphic drivers weren't installed. Well to be honest, they weren't. Because I have VIA/S3g UniChrome Pro IGP graphic card on my motherboard and I couldn't find any drivers for ubuntu. I've got CD with drivers, but there's some shells scripts or something and I can't seem to find any way how to install them. I'm ex-windows user so I need something to double click on, and voila it's installed. I know it's not gonna be that easy. So how to solve my problem? Thanks :]

---

### Post by alexy_ on 2011-08-31
Just can advise to google how-tos for every hardware part you have, starting from video card. If it is not ultra-rare you will find it easily. For examle, first page result from google on "ubuntu VIA/S3g UniChrome Pro IGP" points on this forum's thread: [http://ubuntuforums.org/showthread.php?t=467178](http://ubuntuforums.org/showthread.php?t=467178) Try it, pls.

---

### Post by PHPspirit on 2011-08-31
it didn't work. i can't even change resolution to 1024x768 now ... i'm back where i've been before :[

---

### Post by PHPspirit on 2011-09-01
bump... i need really help with this bcause i dont want XP back.. but my linux is not usable right now under these circumstances :[
my ubuntu is 5x slower than XP ...

---

### Post by alexy_ on 2011-09-01
have you tried to install video driver package? what exactly not working? if you got some kind of error please show them. 
and you are comparing ubuntu without and windows xp with drivers installed.

---

### Post by PHPspirit on 2011-09-02
> **alexy_ said:**
> have you tried to install video driver package? what exactly not working? if you got some kind of error please show them. 
and you are comparing ubuntu without and windows xp with drivers installed.

any errors whatsoever.. the problem is that my ubuntu is so laggy.. internet browser and it's noticable when i'm moving with ubuntu windows it's seriously laggy... or when i'm watching youtube video. yesterday i wanted to watch a dvd movie with my girlfriend but we couldn't bcause some weird lines were going through the entire screen and... what kind of video driver package? i haven't installed anything, bcause i have integrated graphic card via/s3g unichrome pro igp. i was trying everything i found on google and nothing worked.. :(
please help anyone, i don't want to get back to xp i really like ubuntu

---

### Post by alexy_ on 2011-09-02
anyway you should start from installing drivers. first, try this (seems, it is for your chip): [http://ubuntuforums.org/showthread.php?t=467178#3](http://ubuntuforums.org/showthread.php?t=467178#3)

---

### Post by sanderd17 on 2011-09-02
XP can work on lighter machines than Ubuntu (certainly 11.04 is heavy).

Can you post your specs? For Ubuntu you need at least 512 MB ram, but 1GB is recommended.

If you don't have enough RAM, you will better install another flavour of Ubuntu. Lubuntu is made for older devices.

Lubuntu uses the LXDE (Lightweight X11 Desktop Environment) and should work on 128 MB RAM, but 256 is advised.

You can change your Ubuntu installation to a Lubuntu installation if you follow this on psychocats: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

And for the drivers: most drivers are already in the Ubuntu kernel. There is no need to install them. There are exceptions for certain graphical cards (like nVidia) but in general, you don't need to install any drivers.

---

### Post by ofnuts on 2011-09-02
> **sanderd17 said:**
> XP can work on lighter machines than Ubuntu (certainly 11.04 is heavy).

Can you post your specs? For Ubuntu you need at least 512 MB ram, but 1GB is recommended.

If you don't have enough RAM, you will better install another flavour of Ubuntu. Lubuntu is made for older devices.

Lubuntu uses the LXDE (Lightweight X11 Desktop Environment) and should work on 128 MB RAM, but 256 is advised.

You can change your Ubuntu installation to a Lubuntu installation if you follow this on psychocats: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

And for the drivers: most drivers are already in the Ubuntu kernel. There is no need to install them. There are exceptions for certain graphical cards (like nVidia) but in general, you don't need to install any drivers.

Shot in the dark: in the past I had a Linux behave a bit like this. The HDD was not using DMA and this made all disk access slow and very CPU intensive. Use (sudo) hdparm to check if with your HDD, DMA is needed and enabled.

---

### Post by PHPspirit on 2011-09-02
> **alexy_ said:**
> anyway you should start from installing drivers. first, try this (seems, it is for your chip): [http://ubuntuforums.org/showthread.php?t=467178#3](http://ubuntuforums.org/showthread.php?t=467178#3)

it didn't work, this is what it returned:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Couldn't find any package whose name or description matched "xserver-xorg-video-unichrome"
Couldn't find any package whose name or description matched "xserver-xorg-video-unichrome"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 4 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done

```but thanks for the suggestion anyway.

 > **sanderd17 said:**
> XP can work on lighter machines than Ubuntu (certainly 11.04 is heavy).

Can you post your specs? For Ubuntu you need at least 512 MB ram, but 1GB is recommended.

If you don't have enough RAM, you will better install another flavour of Ubuntu. Lubuntu is made for older devices.

Lubuntu uses the LXDE (Lightweight X11 Desktop Environment) and should work on 128 MB RAM, but 256 is advised.

You can change your Ubuntu installation to a Lubuntu installation if you follow this on psychocats: [http://www.psychocats.net/ubuntu/purelxde](http://www.psychocats.net/ubuntu/purelxde)

And for the drivers: most drivers are already in the Ubuntu kernel.  There is no need to install them. There are exceptions for certain  graphical cards (like nVidia) but in general, you don't need to install  any drivers.

I don't really know if it's true that it's because of my specs. On XP I could run games like GTA:SA, WoW without lag on low details and 1024x768. I can't believe that my PC isn't able to run ubuntu. Just my suggestion. Anyways, my specs are 512 mb ram, 2800+ sempron, Samsung HD200HJ HDD, and motherboard asus k8v-mx. It's kinda old PC. I'll try reinstall to Lubuntu asap. Thanks for your help.

> **ofnuts said:**
> Shot in the dark: in the past I had a Linux  behave a bit like this. The HDD was not using DMA and this made all disk  access slow and very CPU intensive. Use (sudo) hdparm to check if with  your HDD, DMA is needed and enablhdparm - get/set hard disk parameters - version v9.15


ed.
When I enter "enablhdparm" it says:
```
enablhdparm command not found
```I thought you've made a spelling mistake "enablEhdparm" so I tried to add that "E" but it doesn't work either. Same error; it says that command wasn't found.
Also when I enter sudo hdparm it returns:
```
hdparm - get/set hard disk parameters - version v9.15

Usage:  hdparm  [options] [device] ..
```and a long list of options. Thanks for your help anyway.
---------------------------------------------------------------------

Another thing: I found the CD with drivers that I got when I bought this PC. On the CD is "Display" folder so I opened it, and there are drivers for Linux too. So in the Linux folder is another "RedHat 9" folder so I'm going to try to install it. Will post my results.

---

### Post by mikejonesey on 2011-09-02
kill the highest cpu users?
```
ps -eo pcpu,comm --sort pcpu | tail -3 | xargs killall
```

---

### Post by ofnuts on 2011-09-02
> **PHPspirit said:**
> When I enter "enablhdparm" it says:
```
enablhdparm command not found
```I thought you've made a spelling mistake "enablEhdparm" so I tried to add that "E" but it doesn't work either. Same error; it says that command wasn't found.
Also when I enter sudo hdparm it returns:
```
hdparm - get/set hard disk parameters - version v9.15

Usage:  hdparm  [options] [device] ..
```and a long list of options. Thanks for your help anyway.

Hmmm. Stray paste, sorry. I meant:
```

sudo hdparm /dev/sda

```
for a start...

---

### Post by PHPspirit on 2011-09-02
> **mikejonesey said:**
> kill the highest cpu users?
 ```
ps -eo pcpu,comm --sort pcpu | tail -3 | xargs killall
```
it just killed only firefox... 

> **ofnuts said:**
> Hmmm. Stray paste, sorry. I meant:
```

sudo hdparm /dev/sda

```for a start...

it returned following:
```

/dev/sda:
 multcount     = 16 (on)
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 24321/255/63, sectors = 390721968, start = 0

```
is that good or bad? :|

---

### Post by ofnuts on 2011-09-02
> **PHPspirit said:**
> 
it returned following:
```

/dev/sda:
 multcount     = 16 (on)
 IO_support    =  0 (default) 
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 24321/255/63, sectors = 390721968, start = 0

```is that good or bad? :|
Mine says:
```

 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 38913/255/63, sectors = 625142448, start = 0

```So mine is bigger than yours :) It is mostly not using 32-bit transfer mode, it seems, which is not so normal. Use :
```
sudo hdparm -i /dev/sda
```to display all your HDD capabilities, and current settings. Mine say:
```

 Model=HITACHI, FwRev=PC3ZC70F, SerialNo=xxxxxxxxxx
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=15151kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=625142448
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

```As you can see my disk is using udma5 mode, and yours should be doing so. If it's listed as using a pio mode then there is your problem.

Besides "man hdparm", I found this page useful:
[http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap6sec74.html](http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap6sec74.html)

---

### Post by PHPspirit on 2011-09-03
> **ofnuts said:**
> Mine says:
```

 multcount     =  0 (off)
 IO_support    =  1 (32-bit)
 readonly      =  0 (off)
 readahead     = 256 (on)
 geometry      = 38913/255/63, sectors = 625142448, start = 0

```So mine is bigger than yours :) It is mostly not using 32-bit transfer mode, it seems, which is not so normal. Use :
```
sudo hdparm -i /dev/sda
```to display all your HDD capabilities, and current settings. Mine say:
```

 Model=HITACHI, FwRev=PC3ZC70F, SerialNo=xxxxxxxxxx
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=15151kB, MaxMultSect=16, MultSect=off
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=625142448
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7

 * signifies the current active mode

```As you can see my disk is using udma5 mode, and yours should be doing so. If it's listed as using a pio mode then there is your problem.

Besides "man hdparm", I found this page useful:
[http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap6sec74.html](http://tldp.org/LDP/solrhe/Securing-Optimizing-Linux-RH-Edition-v1.3/chap6sec74.html)
This is what I've got:
```

 Model=SAMSUNG, FwRev=KF100-06, SerialNo=MySerialNumber
 Config={ Fixed }
 RawCHS=16383/16/63, TrkSize=34902, SectSize=554, ECCbytes=4
 BuffType=DualPortCache, BuffSize=8192kB, MaxMultSect=16, MultSect=16
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=390721968
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 *udma6 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-3,4,5,6,7

 * signifies the current active mode

```I guess my disc is using udma6.. ? is that bad or good? btw. i just realized one thing. i can see only 1 partition of my HDD. when i was installing ubuntu i didnt really know what those settings mean [and i still dont know]. so i set first disc to "ext4" and i set something that had to do with folders to "/" and i set the second partition to fat32 and the main folder or something like that, to "/home/" .. but i cant see the second partition of my disc just first partition. i dont know if i didnt mess up something with this.

---

### Post by ofnuts on 2011-09-03
> **PHPspirit said:**
> I guess my disc is using udma6.. ? is that bad or good? btw. i just realized one thing. i can see only 1 partition of my HDD. when i was installing ubuntu i didnt really know what those settings mean [and i still dont know]. so i set first disc to "ext4" and i set something that had to do with folders to "/" and i set the second partition to fat32 and the main folder or something like that, to "/home/" .. but i cant see the second partition of my disc just first partition. i dont know if i didnt mess up something with this.
Udma6 is OK.

Usually you define at least a swap partition (which has a very specific status and doesn't show in the directory tree), and "/". Past that you can also define a /home, a /usr, a /var...

To check your partitions you can start gparted (Gnome) or partitionmanager (KDE).

But on the whole your hdparm output above seems to invalidate the HDD problem hypothesis and you'll have to look elsewhere.

Finding where you burn all the CPU (and what type of burn it is: system? user? or I/O wait?) is next on the list.

---

