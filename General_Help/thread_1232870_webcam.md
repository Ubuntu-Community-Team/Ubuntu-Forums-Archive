---
title: "webcam"
date: 2009-08-06
forum: General Help
---

### Post by azmo35 on 2009-08-06
:( Hi,help me with this webcam please,i migrate from Ubuntu 8.04 to 9.04 for two reason's to get only on Os so no more need of Windows.The second is this webcam gained some life with Ubuntu 9.04 live cd and not on Ubuntu 8.04,even after instal the driver,see my initial tread [here]("http://ubuntuforums.org/showthread.php?t=1222831").
Now the problem is the webcam works on cheese but is you record a video no sound,and the picture hang for a few seconds on skype no sound and video.
Any help,suggestions or comments will be appreciated,thanks.](*,)

---

### Post by azmo35 on 2009-08-08
](*,)Please,please help me.](*,)

---

### Post by Arup on 2009-08-08
Have you done a fresh install of 9.04 with webcam attached?

---

### Post by khelben1979 on 2009-08-08
What is the model of the webcam?

[Linux UVC driver and tools]("http://linux-uvc.berlios.de/") for a list of supported webcams with Linux.

If it's not the fault of the webcam, then you have the possibility on [downloading the static version of Skype]("http://www.skype.com/go/getskype-linux-static") from Skype.com. You'll haveto unpack the archive and run the executable Skype file manually in this case.

---

### Post by azmo35 on 2009-08-08
Hi, thanks for your reply yes i made a fresh install,but i don't now if the webcam was attach,and the model is criative live cam model vf0470,id-041e:4068, thanks.
run code/
> lsusb

---

### Post by khelben1979 on 2009-08-08
```
lspci
```

It will give us more information about your hardware. Might be useful in order to get a step closer on solving this.

---

### Post by 3rdalbum on 2009-08-08
> **azmo35 said:**
> 
Now the problem is the webcam works on cheese but is you record a video no sound

Cheese doesn't record sound.

---

### Post by dk06 on 2009-08-08
> **azmo35 said:**
> :( Hi,help me with this webcam please,i migrate from Ubuntu 8.04 to 9.04 for two reason's to get only on Os so no more need of Windows.The second is this webcam gained some life with Ubuntu 9.04 live cd and not on Ubuntu 8.04,even after instal the driver,see my initial tread [here]("http://ubuntuforums.org/showthread.php?t=1222831").
Now the problem is the webcam works on cheese but is you record a video no sound,and the picture hang for a few seconds on skype no sound and video.
Any help,suggestions or comments will be appreciated,thanks.](*,)
[URL="https://help.ubuntu.com/community/Webcam"]
https://help.ubuntu.com/community/Webcam[/URL]
[URL="http://tech.shantanugoel.com/2008/05/11/tip-getting-your-webcam-to-work-in-ubuntu.html"]
http://tech.shantanugoel.com/2008/05/11/tip-getting-your-webcam-to-work-in-ubuntu.html[/URL]
[URL="https://wiki.ubuntu.com/SkypeWebCams"][B]
https://wiki.ubuntu.com/SkypeWebCams[/B][/URL]
[URL="http://ubuntuforums.org/showthread.php?t=238820"]
http://ubuntuforums.org/showthread.php?t=238820[/URL]   <--Microphone 
[URL="http://www.howtogeek.com/forum/topic/install-microphone-in-ubuntu"]
http://www.howtogeek.com/forum/topic/install-microphone-in-ubuntu[/URL]
[URL="http://ubuntuforums.org/showthread.php?t=477724"]
http://ubuntuforums.org/showthread.php?t=477724[/URL]   < --Skype Mic

---

### Post by azmo35 on 2009-08-08
Again,my input:
[HTML]azmo@azmo-laptop:~$ lsmod|grep videodev
videodev               41600  1 gspca_main
v4l1_compat            21764  1 videodev
azmo@azmo-laptop:~$ lsusb
Bus 001 Device 003: ID 0951:1624 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 006: ID 04f3:0212 Elan Microelectronics Corp.
Bus 003 Device 008: ID 041e:4068 Creative Technology, Ltd WebCam Live! Notebook 
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
azmo@azmo-laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 04)
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 04)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 04)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 04)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 04)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 04)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d4)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 04)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 04)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 04)
00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 04)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 04)
06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
06:06.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
06:07.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
[/HTML]

---

### Post by khelben1979 on 2009-08-08
Did you try Skype static version?

---

### Post by azmo35 on 2009-08-08
Sorry,no tell me how please:redface: i mean how to install and maybe i have first to unistall skype??
Update,i been read a lot of threads and all info i can found so on skype 2.0.0.72 finally i got the sound working on the test call, this mic is from the webcam, now only need help with video,many thanks so far to that who reply.

---

### Post by azmo35 on 2009-08-08
Thanks so mutch khelben1979 you are right, i used synaptic to uninstall skype, then i found that skype-static 2.0.0.72 "medibuntu package" is on synaptic so that solve my problem with the video, for the sound the settings are wrong in and out i change to pulse on skype settings, test call and it worked, thanks and thanks again,azmo:lolflag:

---

### Post by khelben1979 on 2009-08-08
> **azmo35 said:**
> Thanks so mutch khelben1979 you are right, i used synaptic to uninstall skype, then i found that skype-static 2.0.0.72 "medibuntu package" is on synaptic so that solve my problem with the video, for the sound the settings are wrong in and out i change to pulse on skype settings, test call and it worked, thanks and thanks again,azmo:lolflag:

Always nice to see when problems can be fixed. :)

---

### Post by thatvistunna on 2009-08-09
I found this link very helpful as well for my old webcam that worked in Cheese but not in skype.  Fixed right away:

[https://help.ubuntu.com/community/Webcam#See%20also](https://help.ubuntu.com/community/Webcam#See%20also)

---

