---
title: "SD card reader doesn't mount - Karmic 9.10"
date: 2009-10-31
forum: General Help
---

### Post by pixelot on 2009-10-31
My card reader worked in Jaunty 9.04, but after I upgraded to Karmic yesterday, it doesn't mount like it should. I did a little bit of searching on the problem, and I found some threads that suggested running *dmesg | tail*, so I did that and got this:

> [62814.825123] mmc0: card 0002 removed
[63111.151470] mmc0: new high speed SD card at address 0002
[63115.528177] mmc0: card 0002 removed
[63117.498508] mmc0: new high speed SD card at address 0002
[63125.569679] mmc0: card 0002 removed
[63127.460460] mmc0: new high speed SD card at address 0002
[63178.701133] mmc0: card 0002 removed
[63202.055533] mmc0: new high speed SD card at address 0002
[63323.660130] mmc0: card 0002 removed
[63325.289446] mmc0: new high speed SD card at address 0002


So it looks like it's recognized at least, but a new file doesn't show up in /dev, so I don't know how I would be able to manually mount it. Any suggestions?

TIA,
-pixelot ;)

---

### Post by gadolinio on 2009-10-31
I would try using Disk Manager (the package is disk-manager, and i think it can be found in synaptic). It lets you manage drives-partitions-etc. If your computer can actually use/recognize the hardware, that program might help you mount it (and select where, among other options).
hope you find this useful...

---

### Post by kgarbutt on 2009-10-31
I am experiencing the same problem with my eepc 701. My SD reader worked in jaunty but not in Karmic. Other than that everything is fine so far with karmic. I am waiting for the next release of eee-control though. If anyone has asolution for the card reader problem I would appreciate it. Thanks everyone.

---

### Post by armoftheland on 2009-11-01
hello all,

i'm a bit of a noob, so i don't have any answer for you guys, but i AM having the same problem. as pixelot suggested here's my output of dmesg | tail:

[ 1574.526046] Dev mmcblk0: unable to read RDB block 0
[ 1574.527064]  unable to read partition table
[ 1719.334150] tifm0 : demand removing card from socket 0:1
[ 1719.334223] mmc0: card 8fe4 removed
[ 1857.084153] tifm_core: MMC/SD card detected in socket 0:1
[ 1858.780145] mmc0: error -110 whilst initialising SD card
[ 1916.069272] tifm0 : demand removing card from socket 0:1
[ 1998.688165] tifm_core: MMC/SD card detected in socket 0:1
[ 2000.385135] mmc0: error -110 whilst initialising SD card
[ 2318.049521] tifm0 : demand removing card from socket 0:1

any way to get this up and running? :KS 

EDIT: Guess I should say I'm running 9.10 (hmm duh) on Toshiba Satellite A200 MR4 (b**ches!)

beaches?

---

### Post by Rasiq on 2009-11-01
Same happening here on a ASUS 701 EEEPC

The worse thing is. I cannot access sd card even on gparted. It breaks the system.

Any workaround?

---

### Post by armoftheland on 2009-11-01
ok, so, i left my memory card in my laptop, then let it hibernate. and when it woke up, it decided to recognize the card. Haven't tested if this works consistantly yet... but wtf? maybe itll work for u guys too?

---

### Post by Notselfcreated on 2009-11-02
I'm experiencing the same problem on an Acer Aspire One D150.

EDIT: Nevermind, I'm actually not. Mine shows up in /dev, but it doesn't automatically mount.

---

### Post by adamnr on 2009-11-02
> **pixelot said:**
> My card reader worked in Jaunty 9.04, but after I upgraded to Karmic yesterday, it doesn't mount like it should. I did a little bit of searching on the problem, and I found some threads that suggested running *dmesg | tail*, so I did that and got this:



So it looks like it's recognized at least, but a new file doesn't show up in /dev, so I don't know how I would be able to manually mount it. Any suggestions?

TIA,
-pixelot ;)

I did a fresh install of 9.10 on my eeepc 901 and have the same issue. The SD in the card reader does not mount and cannot be seen by gparted.

---

### Post by pixelot on 2009-11-02
> **armoftheland said:**
> ok, so, i left my memory card in my laptop, then let it hibernate. and when it woke up, it decided to recognize the card. Haven't tested if this works consistantly yet... but wtf? maybe itll work for u guys too?

I just want to caution anyone before trying this... I hibernated and when I started it back up, I only had the Ubuntu +memtest option, and nothing else. I tried reinstalling GRUB from a Live CD and whatnot, but I ended up reinstalling Ubuntu, since I had my /home partition intact. But it was kind of annoying. ;)

---

### Post by colnizster on 2009-11-03
same problem here. i am running kubuntu 9.10. external usb drives work fine but sd cards are not detected/mounted. i found something promising in System Settings -> Advanced Tab -> Device Actions ... but it won't let me add a new parameter. someone please help :confused:

---

### Post by AdamBlue on 2009-11-03
I'm also able to get external drives to work, but not SD cards, or the SD card to be read from my Camera plugged in via USB.  Here's some info if it helps:

> [  517.522367] CE: hpet increasing min_delta_ns to 33750 nsec
[ 2199.848084] CE: hpet increasing min_delta_ns to 50624 nsec
[16029.388190] CE: hpet increasing min_delta_ns to 75936 nsec
[44827.639587] mmc0: new SD card at address fd11
[44827.851014] mmcblk0: unable to set block size to 512: -123
[44827.851031] mmcblk: probe of mmc0:fd11 failed with error -22
[44827.933348] mmc0: card fd11 removed
[44828.983592] mmc0: new SD card at address fd11
[44828.984186] mmcblk0: mmc0:fd11 SD512 488 MiB 
[44828.984244]  mmcblk0: p1

---

### Post by danteuk on 2009-11-09
I have the problem on a Dell Vostro 1710.
Been using a SD card in the slot for about a mouth without problem using 9.04 - upgraded to 9.10 and it seemed okay, then tonight it refused to mount it. I tried another SD, also no luck, also tried a card reader too.
Seems to recognize it but then fails to do anything vaguely useful with it.

dmesg From the card:
```

[ 6123.408242] mmc0: new high speed SDHC card at address 0007
[ 6123.408567] mmcblk0: mmc0:0007 SD4GB 3.74 GiB
[ 6123.408672]  mmcblk0: p1

```

Tried manually mounting it using various fstypes without any joy.
I thought maybe it was corrupt, didn't have a another machine to hand to test on, so I bite the bullet and put it in my camera and reformatted ( 3.5gb of pics I've got to reload - if a when it works again! ).
Still no joy in SD slot or card reader.

dmesg From the reader:
```

[ 5824.035339] scsi 8:0:0:0: Direct-Access     6-in-1   CF/MD            0202 PQ: 0 ANSI: 0 CCS                                     
[ 5824.040165] scsi 8:0:0:1: Direct-Access     6-in-1   SM/SD/MMC/MS     0202 PQ: 0 ANSI: 0 CCS                                     
[ 5824.041305] sd 8:0:0:0: Attached scsi generic sg2 type 0                                                                         
[ 5824.041533] sd 8:0:0:1: Attached scsi generic sg3 type 0                                                                         
[ 5824.129703] sd 8:0:0:0: [sdb] Attached SCSI removable disk                                                                       
[ 5824.134251] sd 8:0:0:1: [sdc] Attached SCSI removable disk                                                                       
[ 5871.032204] usb 3-1: reset full speed USB device using uhci_hcd and address 9                                                    
[ 5890.967073] sd 8:0:0:1: [sdc] 4 512-byte logical blocks: (2.04 kB/2.00 KiB)                                                      
[ 5890.971798] sd 8:0:0:1: [sdc] Assuming drive cache: write through                                                                
[ 5891.090124] usb 3-1: reset full speed USB device using uhci_hcd and address 9                                                    
[ 5891.264892] sd 8:0:0:1: [sdc] Assuming drive cache: write through                                                                
[ 5891.264906]  sdc:                                                                                                                
[ 5922.132606] usb 3-1: reset full speed USB device using uhci_hcd and address 9                                                    
[ 5927.290882] usb 3-1: device descriptor read/64, error -71                                                                        
[ 5927.522837] usb 3-1: device descriptor read/64, error -71                                                                        
[ 5927.760073] usb 3-1: reset full speed USB device using uhci_hcd and address 9                                                    
[ 5927.882660] usb 3-1: device descriptor read/64, error -71                                                                        
[ 5928.134870] usb 3-1: device descriptor read/64, error -71                                                                        
[ 5928.382601] usb 3-1: reset full speed USB device using uhci_hcd and address 9                                                    
[ 5928.802583] usb 3-1: device not accepting address 9, error -71                                                                   
[ 5928.923031] usb 3-1: reset full speed USB device using uhci_hcd and address 9                                                    
[ 5929.342576] usb 3-1: device not accepting address 9, error -71                                                                   

```

Just noticed this in the log from boot:
```

[   11.156940] mmc0: Unknown controller version (2). You may experience problems.
[   11.156992] Registered led device: mmc0::
[   11.157039] mmc0: SDHCI controller on PCI [0000:08:05.2] using DMA
[   11.491506] mmc0: new high speed SDHC card at address 0007
[   11.673227] mmcblk0: mmc0:0007 SD4GB 3.74 GiB
[   11.673274]  mmcblk0: p1

```

Anyone got any ideas on this ?

---

### Post by sgornick on 2009-11-10
Not sure if this is identical to my problem as mine shows "device descriptor read/64, error -110" and yours shows a different error code but I filed bug report #479829 for mine.

[https://bugs.launchpad.net/ubuntu/+bug/479829](https://bugs.launchpad.net/ubuntu/+bug/479829)

---

### Post by colnizster on 2009-11-10
ok so I got my SD cards mounting and reading now. here's what i did -

powered down

disconnected multi-card reader from motherboard

powered up and let run up to kubuntu login screen

powered down

plugged multi-card reader back into motherboard

powered up

logged in, inserted SD card, and VOILA! (NOT VIOLA)

oh and i also went into my BIOS and removed FLOPPY DRIVE from the boot priority (because there isn't one installed - not sure if this affected the SD issue or not...)


i know this is an odd fix and it seems strange that installing karmic caused the issue but whatever i got it working.

---

### Post by Candlescandles on 2009-11-23
Wow.  That just worked for me.  I shut down, unplugged, rebooted and plugged in with the system on.  Everything was detected!  Thanks :D

---

### Post by djbitty on 2009-12-24
I too am currently having the same problem with the SD card reader.  I tried the power down and disconnecting sequence listed above, however it did not work for me.  If anyone has another solution to this problem, please advise.  Thank you!

---

### Post by Jeanfrancoissven on 2009-12-30
This post worked great for me on my dell studio:
[http://danilogurovich.wordpress.com/2009/12/09/ubuntu-karmic-koala-9-10-wheres-my-sd-card/#comment-1997](http://danilogurovich.wordpress.com/2009/12/09/ubuntu-karmic-koala-9-10-wheres-my-sd-card/#comment-1997)

---

### Post by mrplavius on 2010-01-25
I had the same problem. elsewhere I found a tip and it worked on my eeepc 701...

Simply disable your card reader on bios... save it, log on linux...
Of course you'll not see it now...
restart and reenable it on bios... it should work now...
At least here it did! I hope it helps you!!! :D

---

### Post by ironside on 2010-02-07
Ok I have the same problem with my SD reader not working. I am new to Ubuntu so not sure on the commands but I have searched and searched and haven't been able to fix it. Anyone willing to help?

---

### Post by Teh_Messiah on 2010-11-02
I dont have an option in my bios to disable the sd card reader, 
It is hard soldiered to the motherboard of my wind U100 Netbook,
I used it only an hour ago to make a live usb of 10.10 netbook remix,
I even rebooted to windows and windows didn't even recognise it,
I have rebooted several times,
I tried the fix from [http://danilogurovich.wordpress.com/2009/12/09/ubuntu-karmic-koala-9-10-wheres-my-sd-card/#comment-1997]("http://danilogurovich.wordpress.com/2009/12/09/ubuntu-karmic-koala-9-10-wheres-my-sd-card/#comment-1997") restarted and it didn't fix it.
I asked my IT linux guru lecturer at tafe who, after checking if hald was running couldn't figure it out either.

```
ben@lappy:~$ dmesg | tail
[ 1706.390955] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1586
[ 1786.385176] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 2219
[ 1866.391178] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 2061
[ 1946.385195] ===>rt_ioctl_giwscan. 10(10) BSS returned, data->length = 1584
[ 2026.383631] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1902
[ 2106.384215] ===>rt_ioctl_giwscan. 14(14) BSS returned, data->length = 2219
[ 2186.390239] ===>rt_ioctl_giwscan. 9(9) BSS returned, data->length = 1426
[ 2266.389107] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1902
[ 2346.389223] ===>rt_ioctl_giwscan. 12(12) BSS returned, data->length = 1903
[ 2426.387393] ===>rt_ioctl_giwscan. 13(13) BSS returned, data->length = 2061
```

I then had to go home from college and hibernated the netbook, (hibernate fix, mentioned earlier) turned it back on when i got home and it worked!

now all i have to do is figure out how to unlock a locked micro sd card!

---

