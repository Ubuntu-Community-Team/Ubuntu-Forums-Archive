---
title: "laptop keeps freezing and hanging.."
date: 2012-06-07
forum: General Help
---

### Post by lindaonline15 on 2012-06-07
hi..

I'm having so much of problem with ubuntu 12.04.
my laptop gets freezed from time to time, (few times per hour!) and nothing works so I have to make a forced shut down! (and nicely loose all the work!!)

this is so ugly... and apparently many ppl are having this pickle!!
really appreciate it if someone could give me guidance to clear this mess up! :)

btw, my laptop specs:
```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port 
(rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipse
t HECI Controller (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enh
anced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Defin
ition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express 
Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express 
Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express 
Root Port 3 (rev 05)
00:1c.5 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express 
Root Port 6 (rev 05)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enh
anced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Con
troller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port 
SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller 
(rev 05)
01:00.0 VGA compatible controller: Advanced Micro Devices [AMD] nee ATI Manhatt
an [Mobility Radeon HD 5400 Series]
01:00.1 Audio device: Advanced Micro Devices [AMD] nee ATI Cedar HDMI Audio [Ra
deon HD 5400/6300 Series]
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network
 Adapter (PCI-Express) (rev 01)
03:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
03:00.1 System peripheral: Ricoh Co Ltd Memory Stick Host Controller
03:00.4 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller
04:00.0 Ethernet controller: Marvell Technology Group Ltd. Yukon Optima 88E8059
 [PCIe Gigabit Ethernet Controller with AVB] (rev 11)
3f:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Ge
neric Non-core Registers (rev 02)
3f:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture Sy
stem Address Decoder (rev 02)
3f:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
3f:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
3f:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
3f:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)


```

---

### Post by lindaonline15 on 2012-06-07
I have to add:
1. I have already uninstall and reinstall back the proprietary drivers,
2. previously i had many desktop effects enabled so i already rollback to default by  running ```
unity --reset
```
3. i recently upgraded my RAM from 4GB to 16GB and I think freezing happens even more.. I ran memtest and seemed no problem with that.
4. I've checked my HD health using SMART and its fine..
5. the weirdest part is when it freezes, the Capslock, and Scrolllock keep blinking together!!

---

### Post by devxdev on 2012-06-07
I'd suggest backing up all your data on Ubuntu and doing a fresh install; an that is quite the RAM upgrade, maybe swap needed an adjustment? are you x64 or x86?

---

### Post by lindaonline15 on 2012-06-07
x64...
and right now my swap is 8GB...

---

### Post by devxdev on 2012-06-07
> **lindaonline15 said:**
> x64...
and right now my swap is 8GB...

Strange that sounds right, e.g. the .5 of your actual ram..
*lost* hopefully someone can help you with another option besides a reformat :( sorry I just saw you ask from IRC ):P

---

### Post by lindaonline15 on 2012-06-07
> **devxdev said:**
> Strange that sounds right, e.g. the .5 of your actual ram..
*lost* hopefully someone can help you with another option besides a reformat :( sorry I just saw you ask from IRC ):P

thats all right :)
thanks for trying anyways :) if nothing also i'll have the reformat solution in my head.. ;)

---

### Post by sanderj on 2012-06-08
> **lindaonline15 said:**
> 
5. the weirdest part is when it freezes, the Capslock, and Scrolllock keep blinking together!!

See (FWIW) [http://www.linuxquestions.org/questions/linux-general-1/caps-lock-and-scroll-lock-flashing-47433/](http://www.linuxquestions.org/questions/linux-general-1/caps-lock-and-scroll-lock-flashing-47433/)

---

### Post by lindaonline15 on 2012-06-08
thanks for the link...
assuming it is a kernel panic, what should i do?

---

### Post by sanderj on 2012-06-08
> **lindaonline15 said:**
> thanks for the link...
assuming it is a kernel panic, what should i do?


Keep memtest86 running for at least one night.

If that does  not reveal problems, try a different version (older and/or newerver) of ubuntu

---

### Post by Mark Phelps on 2012-06-09
Noticed the linked article in post #7 mentioned heat as a possible problem -- especially the CPU overheating.

Are you noticing your laptop getting unduly warm just before it freezes?

---

### Post by Curious00 on 2012-06-09
Me too. I can't use 12.04 at all, because it freezes constantly. You might try 11.10. That works well for me.

---

### Post by lindaonline15 on 2012-06-09
> **sanderj said:**
> Keep memtest86 running for at least one night.

If that does  not reveal problems, try a different version (older and/or newerver) of ubuntu

when i run memtests, suddenly goes off which i dont know its a good sign or bad..
so i took video and uploaded so if you can watch and tell me if this is ok...
[http://s1261.photobucket.com/albums/ii582/lindaonline15/?action=view&current=VIDEO0139-0.mp4](http://s1261.photobucket.com/albums/ii582/lindaonline15/?action=view&current=VIDEO0139-0.mp4)

---

### Post by lindaonline15 on 2012-06-09
> **Mark Phelps said:**
> Noticed the linked article in post #7 mentioned heat as a possible problem -- especially the CPU overheating.

Are you noticing your laptop getting unduly warm just before it freezes?

i did have the overheating problem overall it never was below 60C, but after i re-installed proprietary drivers as well as turining off effects, its abit better now... but just ABIT, not much...

---

### Post by sanderj on 2012-06-09
> **lindaonline15 said:**
> when i run memtests, suddenly goes off which i dont know its a good sign or bad..
so i took video and uploaded so if you can watch and tell me if this is ok...
[http://s1261.photobucket.com/albums/ii582/lindaonline15/?action=view&current=VIDEO0139-0.mp4](http://s1261.photobucket.com/albums/ii582/lindaonline15/?action=view&current=VIDEO0139-0.mp4)

That's a very bad sign. If it even can't run memtest, I would swap the computer completely.

---

### Post by lindaonline15 on 2012-06-09
> **sanderj said:**
> That's a very bad sign. If it even can't run memtest, I would swap the computer completely.

did you watch the video? it runs it but in the middle goes off..

---

### Post by sanderj on 2012-06-09
> **lindaonline15 said:**
> did you watch the video? it runs it but in the middle goes off..

Exactly. That's very bad.

EDIT: and not related to the OS or a driver; it's something very bad with the hardware itself. Might be RAM, but also CPU or PSU. So therefor my advice: completely swap the computer with the supplier.

HTH

---

### Post by holycow131415 on 2012-06-10
Take 1 stick of ram out and try to run it again (leaving you with 8 gb ram). if it turns off, or runs through, swap it with the other stick of ram to see if one stick is bad.

---

### Post by lindaonline15 on 2012-06-19
ok... thanks both of you guys for the help.. sry i couldnt come here sooner to report the results...
yes as it turned out, problem WAS the RAM... so i did test each 8G stick seperately, same results and finally i switched back to my old 4G rams (2 of 2G) and memorytest kept running for hours without any errors or any weired behaviour like before...
anyways, now I have two problems left:
[LIST]Laptop's temperature is still always HOT! yes if I dont do anything it'll be around 58C but once i start a simple movie, or specially any write operation or just run one of my VMs, easily rises up to 75C!! (which I understand is not related to this topic so im gonna put it in the proper place...)
[/LIST]
[LIST]the freezing on normal situations is gone but I still get a BIG FAT FREEZE when I connect projector (or for that matter, any kind of external display) to my laptop!
[/LIST]

what to do with that... ?

---

