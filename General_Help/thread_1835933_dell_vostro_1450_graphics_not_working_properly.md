---
title: "dell vostro 1450 graphics not working properly"
date: 2011-08-30
forum: General Help
---

### Post by ubun2warrior on 2011-08-30
hi

i recently purchased a dell vostro 1450 laptop, it came preloaded with ubuntu 10.10. the config of the laptop is -
corei3, 2gb ram, 320 gb hd, 14inch screen, intel corp sandy bridge integrated graphics.
its working fine but , the visual effects are not working, when i go to system>preferences appearance>visual effects and change it to normal or extra it does not change.

kindly help , whats the problem?

regards
ubun2warrior

---

### Post by ubun2warrior on 2011-08-31
My system is updated also, yet the visual effects can't be enabled, its  really very annoying...

i have faced similar problem with nvidia-graphics but there i could easily install the drivers and the visual effects could be enabled but here there are no additional drivers to install apart from broadcom wireless which is already installed..

i searched google also there's no help available, the first link that i get on google is this very thread which i started...

F1 F1 F1

Note: F1 = HELP  :)

---

### Post by ubun2warrior on 2011-08-31
hi

i tried fedora 15 live, its working fine with full graphics... and i think ubuntu 11.04 will also be working fine, i think there is some issue with linux kernel or something maybe... like on my old laptop ubuntu 11.04 and fedora just gave a black screen after booting... and when i i booted with nomodeset = 1 it was up and running but in low graphics mode.

so may be now the older versions of ubuntu and fedora linux have some issues with new hardware like core i3, etc.

my system has core i3 and sandy bridge integrated graphics

can someone plz suggest some fix for this bcoz i am sure that it must work.. there's always some solution:)

ubun2warrior

---

### Post by ubun2warrior on 2011-08-31
hi

i recently purchased a dell vostro 1450 laptop, it came preloaded with ubuntu 10.10. the config of the laptop is - corei3, 2gb ram, 320 gb hd, 14inch screen, intel corp sandy bridge integrated graphics.
its working fine but , the visual effects are not working, when i go to system>preferences appearance>visual effects and change it to normal or extra it does not change.

My system is also updated, yet the visual effects can't be enabled, its really very annoying...

i have faced similar problem with nvidia-graphics but there i could easily install the drivers and the visual effects could be enabled but here there are no additional drivers to install apart from broadcom wireless which is already installed..

i searched google also there's no help available, the first link that i get on google is this very thread which i started...

i even tried fedora 15 live, its working fine with full graphics... and i think ubuntu 11.04 will also be working fine, i think there is some issue with linux kernel or something maybe... like on my old laptop ubuntu 11.04 and fedora just gave a black screen after booting... and when i i booted with nomodeset = 1 it was up and running but in low graphics mode.

so may be now the older versions of ubuntu and fedora linux have some issues with new hardware like core i3, etc.

can someone plz suggest some fix for this bcoz i am sure that it must work.. there's always some solution !

ubun2warrior

---

### Post by dino99 on 2011-08-31
no need of multiple threads for the same issue.

[http://ubuntuforums.org/showthread.php?p=11204341](http://ubuntuforums.org/showthread.php?p=11204341)

which intel chipset it is ?

---

### Post by realzippy on 2011-08-31
show
```
lspci |grep VGA
```

and for kernel
```
uname -r
```

...should at least use 2.6.38.x for
Intel Corporation Core Processor Integrated Graphics Controller

---

### Post by ubun2warrior on 2011-08-31
> **realzippy said:**
> show
```
lspci |grep VGA
```

and for kernel
```
uname -r
```

...should at least use 2.6.38.x for
Intel Corporation Core Processor Integrated Graphics Controller

hi

thanks for replying..
the system has intel corporation sandy bridge integrated graphics.

and the kerel is not 2.6.38.x its slightly less..

i tried ubuntu 11.04 live the graphics was detected...

so that sorts out the graphic problem..

now i added cpu frequency and scaling monitor to the panel, by default it was set to performance mode.. and my battery was getting drained quiet quickly was it due to this? now i have changed it to on demand..

also i have one more question should i continue using ubuntu 10.10(provided my laptop doesn't get damaged) or i use windows 7(which i will hate whole heartedly but might use if it saves my laptop from being damaged..)

the laptop is providing hardly 2 hrs of back up although it should provide atleast 3.5 to 4 hours( the type of work i do mostly word, emails, ppts, etc)

plz reply quickly.. its urgent.. i don't want to burn my laptop..

ubun2warrior

---

### Post by realzippy on 2011-08-31
please show

```
lspci |grep VGA

```
(didn't ask for fun  ;-)  )

Why should your laptop get damaged?
Too hot?

---

### Post by ubun2warrior on 2011-08-31
hi

this is the output of lspci | grep VGA

> 00:02.0 VGA compatible controller: Intel Corporation Sandy Bridge Integrated Graphics Controller (rev 09)

no it does not get too hot but the battery seems to drain rapidly and the cooling fan seems to be overworked..

the output of uname -r 

> 2.6.35-30-generic

regards

---

### Post by ubun2warrior on 2011-08-31
> **dino99 said:**
> no need of multiple threads for the same issue.

[http://ubuntuforums.org/showthread.php?p=11204341](http://ubuntuforums.org/showthread.php?p=11204341)

which intel chipset it is ?

some details for more clarification
> 
PROCESSOR
Processor	2nd Generation Core i3
Variant	2310M
Chipset	Intel Mobile HM 67 Express
Brand	Intel
Clock Speed	2.1 GHz
Cache	3 MB
MEMORY
Expandable Memory	Up to 8 GB
Memory Slots	2 (Unused Slot - 0)
System Memory	2 GB DDR3
STORAGE
Hardware Interface	SATA
RPM	5400 rpm
HDD Capacity	320 GB
OPTICAL DISK DRIVE
Optical Drive	DVD RW
PLATFORM
Operating System	Free DOS
DISPLAY
Screen Size	14.1 Inch
Resolution	1366 x 768 Pixel
Screen Type	HD WLED Anti-Glare Display
GRAPHICS
Graphic Processor	Standard Intel HD Graphics
INPUT
Web Camera	1.3 megapixel
Pointer Device	TouchPad
Keyboard	Standard Keyboard
AUDIO
Internal Mic	Yes
Speakers	Integrated Stereo Sound
COMMUNICATION
Ethernet	Integrated 10/100 Ethernet LAN
Wireless LAN	802.11 b/g/n
Bluetooth	Combo V3.0
POWER
Battery Backup	Up to 3 hours
Battery Cell	6-cell
Power Supply	65W AC Adapter
PORTS/SLOTS
USB Port	3 x USB 2.0
Mic In	Yes
RJ45 LAN	Yes
HDMI Port	Yes
VGA Port	Yes
Multi Card Slot	3-in-1 Card Reader
MACHINE DIMENSIONS
Weight	2.2 kg
Dimension	342 x 244 x 34.7 mm
Color	Grey
WARRANTY
Warranty	1 year domestic Complete Cover
IN THE BOX
Sales Package	Laptop,Battery,AC Adapter,User Guides and Manuals

---

### Post by ubun2warrior on 2011-09-01
> **realzippy said:**
> show
```
lspci |grep VGA
```

and for kernel
```
uname -r
```

...should at least use 2.6.38.x for
Intel Corporation Core Processor Integrated Graphics Controller


how do i upgrade my kernel??

---

### Post by realzippy on 2011-09-01
```
sudo add-apt-repository ppa:kernel-ppa/ppa
```
```
sudo apt-get update
```
```
sudo apt-get install linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic
```
reboot

---

### Post by ubun2warrior on 2011-09-01
> **realzippy said:**
> ```
sudo add-apt-repository ppa:kernel-ppa/ppa
``````
sudo apt-get update
``````
sudo apt-get install linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic
```reboot

its not working this is the error that i get..

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-2.6.38-8-generic
E: Couldn't find any package by regex 'linux-headers-2.6.38-8-generic'
E: Unable to locate package linux-image-2.6.38-8-generic
E: Couldn't find any package by regex 'linux-image-2.6.38-8-generic'

regards

---

### Post by realzippy on 2011-09-01
..then the software ppa is down I guess.
You have to install manually then.
You run 64 or 32 bit (guess 64)?

---

### Post by ubun2warrior on 2011-09-01
i run 32  bit ubuntu 10.10 it came preloaded with my laptop dell which i purchased few days back...
should i upgrade to 11.04 64bit... the system specs i have mentioned in one of the posts above.. what do you suggest.. it some dell utilities pre installed.. so i am just sticking to it right now, but if u suggest that upgrading would be better, i will go with it.. also i have added a cpu frequency and scaling monitor and by default it is set to performance mode and always shows my usage as 100%.. i have to change it every time to powersaver or on demand.

can i add dell utilities in ubuntu 11.04 also..

---

### Post by deserthowler on 2011-09-01
The 2.6,38 is available through Synaptic in Ubuntu 10.04.
This might be better than playing with PPAs.

Earl

---

### Post by realzippy on 2011-09-01
[B]EDIT: Just see *deserthowler's* post.Didn't know that,not running 10.10.
So open synaptic and search that kernel and install it
[/B]
You only have 2 GB RAM,so stay with 32bit.It is no disadvantage.
Btw,I have no idea about the dell specific stuff.Suggest we go on,
if you don't like the result,you can run a fresh install then.

Edit:
**Don't run following commands if you installed kernel as *deserthowler* suggests.**

```
cd Downloads
```

```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/linux-headers-2.6.38-02063808_2.6.38-02063808.201106040910_all.deb
```
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/linux-headers-2.6.38-02063808-generic_2.6.38-02063808.201106040910_i386.deb
```
```
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.38.8-natty/linux-image-2.6.38-02063808-generic_2.6.38-02063808.201106040910_i386.deb
```

```
sudo dpkg -i linux-headers-2.6.38-02063808_2.6.38-02063808.201106040910_all.deb
```
```
sudo dpkg -i linux-headers-2.6.38-02063808-generic_2.6.38-02063808.201106040910_i386.deb
```
```
sudo dpkg -i linux-image-2.6.38-02063808-generic_2.6.38-02063808.201106040910_i386.deb
```

You also may need fresher versions of *libdrm*,*mesa*,aso. **!**

Easy way to get it is adding xorgedgers ppa;since those guys don't
want giving instructions how to install without reading their page
[I]** Please do not publish instructions for how to install from this archive without linking to this page! Anyone using packages from this archive is expected to read this page first and it is recommended to check back occasionally for notice on problems that may arise. **
[/I]
[visit them]("https://launchpad.net/~xorg-edgers/+archive/ppa/+index?field.series_filter=maverick&batch=75&direction=backwards&memo=75"),read,then post and we go on.

---

### Post by realzippy on 2011-09-01
@ deserthowler

..and how to update libdrm,mesa,xorg-intel aso.
without "playing with ppas" **?**

Btw,if 2.6.38 was available,then
```
sudo apt-get install linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic
```
should have worked,don't you think?
Proposed,backports ?

---

### Post by realzippy on 2011-09-01
@ubun2warrior

We could wait for deserthowler's answer,or ....just go on.?

---

### Post by ubun2warrior on 2011-09-01
oh sorry i  logged out..

actually i have some work to do i will try what realzippy suggested... and as soon as i get some success i will come back..

logging off for now bye..

---

### Post by realzippy on 2011-09-01
since derserthowler disappeared,we go on with post #17.
Ignore my edits.

---

### Post by deserthowler on 2011-09-01
> **realzippy said:**
> @ deserthowler

..and how to update libdrm,mesa,xorg-intel aso.
without "playing with ppas" **?**

Btw,if 2.6.38 was available,then
```
sudo apt-get install linux-headers-2.6.38-8-generic linux-image-2.6.38-8-generic
```
should have worked,don't you think?
Proposed,backports ?

I have it listed in synaptic.  
lucid-updates/main(us.archive.ubuntu.com)
linux-image-2.6.38-10-generic

It is OK to use synaptic.  Really it is.  Synaptic isn't too techie.

Earl

---

### Post by realzippy on 2011-09-01
@ubun2warrior
so try
```
sudo apt-get install linux-headers-2.6.38-10-generic linux-image-2.6.38-10-generic
```

or open synaptic,search for the kernel,mark it to be installed,hit "apply"....

---

### Post by ubun2warrior on 2011-09-02
hi

this is my new output of uname -r

> 2.6.38-8-generic
still my desktop effects cannot be enabled..

---

### Post by ubun2warrior on 2011-09-02
i will now install ubuntu 11.04 on my system... as i said earlier i tried a live disk and it seemed to work fine..

so thanks a lot for ur help

---

### Post by realzippy on 2011-09-02
As mentioned,you had to update libdrm,mesa,xorg-intel also
to make your graphics work...
Since you decided to upgrade to 11.04,this is obsolete.
Good luck & have fun!

---

