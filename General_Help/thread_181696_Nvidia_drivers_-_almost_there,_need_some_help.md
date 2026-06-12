---
title: "Nvidia drivers - almost there, need some help"
date: 2006-05-24
forum: General Help
---

### Post by oofnik on 2006-05-24
Well I've been messing with Ubuntu for about a year now, and I've learned so much about linux and computers in general and I'm loving it. :D 
One of the issues I've been struggling with the entire time however is the nvidia driver. I have a Geforce 5700 card, and when the drivers work, it's awesome. But when they don't, it is pretty far from awesome.

Anyway, I found some new program that I wanted to try out but it required GL, so I decided to go back and mess with the nvidia driver because up until now I've been fine with the packaged nv driver. I install the latest version, 8762, from the nvidia site, modify xorg.conf, and bingo. But when I reboot, it dies. I tried for a while to figure out what was going on but never really found a solution. Well, you know how they say you'll find things when you least expect them.. I did some more investigating and found out what was preventing the nvidia driver from loading. When I changed "Driver" to nvidia, the system would still use the original 7667 version that is packaged with Ubuntu instead of the freshly compiled 8762 module, as evidenced by the system log:
```
[4294790.995000] NVRM: loading NVIDIA Linux x86 NVIDIA Kernel Module  [COLOR="Red"]1.0-7667[/COLOR] Fri Jun 17 07:01:04 PDT 2005
```

Well after X died, I checked the logs, and found this:
```

(II) NVIDIA X Driver  [COLOR="Red"]1.0-8762[/COLOR]  Mon May 15 13:09:21 PDT 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
------*snip*--------
(EE) NVIDIA(0): Failed to initialize the NVIDIA kernel module! Please ensure
(EE) NVIDIA(0):     that there is a supported NVIDIA GPU in this system, and
(EE) NVIDIA(0):     that the NVIDIA device files have been created properly.
(EE) NVIDIA(0):     Please consult the NVIDIA README for details.
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.

```

So basically what's going on I guess is X knows to use the 8762 module, but the system is still loading the old 7667 module somewhere along the line. I'm trying to line up the times but I can't seem to figure that out yet... way too many log files ](*,) 

But yeah, it's a version mismatch. I see this in dmesg directly after 7667 is loaded:
```

May 24 16:28:25 oofnik kernel: [4294810.609000] NVRM: RM/client version mismatch!!
May 24 16:28:25 oofnik kernel: [4294810.609000] NVRM:    aborting to avoid catastrophe!
May 24 16:28:27 oofnik gdm[9800]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
May 24 16:28:30 oofnik kernel: [4294814.871000] NVRM: RM/client version mismatch!!
May 24 16:28:30 oofnik kernel: [4294814.871000] NVRM:    aborting to avoid catastrophe!
May 24 16:28:31 oofnik gdm[9820]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0
May 24 16:28:34 oofnik kernel: [4294819.132000] NVRM: RM/client version mismatch!!
May 24 16:28:34 oofnik kernel: [4294819.132000] NVRM:    aborting to avoid catastrophe!
May 24 16:28:35 oofnik gdm[9838]: gdm_slave_xioerror_handler: Fatal X error - Restarting :0

``` That's gdm trying to load X three times and failing. So, I did 
```
rmmod nvidia
 modprobe /lib/modules/2.6.12-10-686-smp/kernel/drivers/video/nvidia.ko

```
and checked dmesg, and bingo, it loads the correct version:
```
May 24 16:32:26 oofnik kernel: [4295051.244000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-8762  Mon May 15 13:06:38 PDT 2006
``` After that I restart gdm and everything works great.

Sorry to post all that code.. but my question to you is, how can I prevent the system from loading that old nvidia driver, and loading the new one instead? Where the heck is it anyway? I looked for all instances of nvidia.ko and that's the only one I could find. So what to do? Thanks!

---

### Post by Dr. Nick on 2006-05-24
how exactly did you remove the packaged nvidia drivers? Did you search synaptic and remove all packages with nvidia in the name? you could also search your ard drive for the word nvidia and remove the driver file that is packaged if removing it in synaptic doesnt work

---

### Post by oofnik on 2006-05-24
I didn't want to remove the nvidia packages because that gets rid of ubuntu-desktop, then I would have to go and reinstall everything again. I just searched for everything containing nvidia and remove any driver files I found (.o and .ko). Thanks.

---

### Post by Dr. Nick on 2006-05-24
[quote=oofnik]I didn't want to remove the nvidia packages because that gets rid of ubuntu-desktop, then I would have to go and reinstall everything again. I just searched for everything containing nvidia and remove any driver files I found (.o and .ko). Thanks.[/quote]

Ohh Dont worry about ubuntu-desktop, it wont remove everything. It is just a metapackage. Basically what it is their for is to simplify installation. If you install ubuntu-desktop it will automatically select all default ubuntu packages to make it easier. You can safely remove it. If you do this in synaptic it will show you at the bottom of the screen how much space will be freed. For me to remove ubuntu-desktop frees 48k of space, Obviusly not the entire system.

The only caution to removing it is when you upgrade. If you plan to do a fuil system update then reinstall it so it will automatically select all the new programs and stuff from the new version

---

### Post by tseliot on 2006-05-27
You can try my script:
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

It will install the driver and solve you problem with the drivers for you.

---

### Post by oofnik on 2006-06-01
Thanks tseliot, I was looking for a link to your script but never found one. I did get it to work without the script however. I just had to run depmod to change the path to the nvidia module after the old was was uninstalled.
I have one more problem with the nvidia driver though. I can't kill the X server (ctrl+alt+bksp) and I can't run any of the virtual consoles (ctrl+alt+F1..) without the system crapping out. I get a bunch of garbled characters on the screen and then it just crashes and I have to reboot. Any ideas about this?
Thanks again for any help.

---

### Post by oofnik on 2006-06-05
bump.. anyone??

---

### Post by Dr. Nick on 2006-06-07
Not exactly sure, The only time I had "garbled" screen was when my color depth was off in the xorg.conf.

*bump* hoping someone who knows for certain sees it.

---

