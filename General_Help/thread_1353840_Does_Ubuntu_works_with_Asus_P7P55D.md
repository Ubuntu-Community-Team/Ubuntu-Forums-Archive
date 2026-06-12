---
title: "Does Ubuntu works with Asus P7P55D?"
date: 2009-12-13
forum: General Help
---

### Post by Linux69 on 2009-12-13
[SIZE=4]I want to buy a computer with P7P55D board. I'm not sure whether it works with Ubuntu. As a result of Google Search I found out that the JMicron JMB363 PATA ans SATA controller  seems to work. Also the VT1828S 8-Channel  High Definition Audio CODEC seems to work. I found the following Thread in the german Ubuntu forum:

[http://forum.ubuntuusers.de/topic/via-vt1828s/#post-2245662](http://forum.ubuntuusers.de/topic/via-vt1828s/#post-2245662)

What about the Realtek 8112L Gigabit LAN controller? I did not find any coment in regard to exactly that chipset. Also I didn't find out whether the VIA  6308P IEEE 1394 controller is supported.

Thank you.
[/SIZE]

---

### Post by eyrieowl on 2009-12-17
I'm running 9.10 on a p7p55d mobo with a gforce gtx 260 and i7 850.  So works, and works pretty nicely.  The only caveat is that I've thus far been unable to get the sensors to detect properly so I haven't been able to get the fans under control, which means it runs a bit louder than I'd like.  I have faith that this will get fixed eventually, but it's a bit of a pain at the moment.

---

### Post by Dr.Drago on 2009-12-23
I'am running 9.04 on the same P7P55D and I am unable to record via the microphone. I've tried many mixer settings, but without success. Any ideas?

---

### Post by khelben1979 on 2009-12-23
> **Dr.Drago said:**
> I'am running 9.04 on the same P7P55D and I am unable to record via the microphone. I've tried many mixer settings, but without success. Any ideas?

[Pulse audio]("http://en.wikipedia.org/wiki/Pulse_audio").

I have experience with installing Ubuntu Hardy on an ASUS laptop and it worked, as well as using the microphone together with pulse audio.

---

### Post by AkiraBergman on 2009-12-24
I have Ubuntu 9.10 Karmic running on P7P55D-E with i5. 8.04 does not work at all. 8.10 kind of works with shaky Ethernet and slow graphics.

I have not been able to get the onboard microphone working. 

USB Logitech QuickCam Pro 9000 webcam with microphone works. I use it with Skype.

Creative Live sound card microphone works.

---

### Post by AkiraBergman on 2009-12-24
This fixed my microphone problem;

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359)

---

### Post by tbeals31 on 2009-12-24
I'm running Kubuntu 9.10 on an Asus P7P55D EVO, LGA 1156 with a quad-core i7-860 and  EVGA GTX 260 video.  New build over the U.S. Thanksgiving holiday.

Had no problems with install of "AMD"64 Ubuntu.  Video, networking worked immediately.  Still no audio but I am hoping that is a matter of finding the right drivers.  I'm getting the machine configured as time allows.  My last Linux was 32 bit openSUSE on an ancient machine built 6+ years ago; I'm still a newbie for this OS and its packages.

Best of luck with your build,

Cheers

---

### Post by kotakotakota on 2009-12-28
I have had issues with the 3D acceleration which ended up being ridiculously slow on the Asus P7P55D with both the Geforce 9800gt and 9600gt.... I don't know what the issue is, but if anyone knows of a fix, I would appreciate it.  The audio and all the other devices work fine from the start though.  I would recommend this one if there is a fix for that one thing...

---

### Post by iains on 2010-01-28
I've had a new system with P5P55D motherboard, I5 750, 4Gb and nVidia 9600GT graphics. I'm running Ubuntu 9.10 64bit. (also dual boot with Win 7 - supplier/builder/friend was happier with that).

I had no microphone input on either Ubuntu or Win 7. Supplier came on line and used Win 7 Via HD Vdeck program to change settings - now works on both OSes. Maybe same solution as 
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/474359)
(described earlier).

I'm running VM Workstation with guest XP Pro for those things we (sadly) need Windows for.

---

### Post by Pastortom on 2010-03-22
I've got an Asus P7P55Deluxe motherboard, with i5 cpu and 2x2 Corsair Dominator rams.,. And Ubuntu 10.04 and 9.10 doesnt work at all with network settings (it boots and looks fine, but network doesnt work at all)..

This, as far as I know, is due to Ubuntu loading the wrong kernel driver for RealTek 8111/8186B network card.. 

So, if you have 8111 network card, as far as I know at this moment, you will have HELL infront of you, if you try to install Ubuntu on it..

Personally sat 12 hours now, messing about this, Im actually installing Windows XP just to make sure the network card still works Oo

---

### Post by Sciamano on 2010-04-08
@ eyrieowl: I had the same problem of fan loudness until I installed NVIDIA proprietary drivers. As soon as I did that, the loudness ceased (it was probably caused by the video card's fan).
I tell you just in case you have an NVIDIA card, and want to try...

What is not working for me is the KSysGuard system monitor: it shows no CPU load percentage, nor any network traffic.

---

### Post by tetsuo76 on 2010-06-11
I am having the same problem with the network card of that motherboard. I have windows7 on another partition and I have noticed that after upgrading to 10 I am having exactly the same problem on Windows too!! Ubuntu 10 is a virus!! hehe

---

### Post by AkiraBergman on 2010-06-11
My mobo is ASUS-P7P55D-E and it works well with Ubuntu-10-04. The mic problem was still there but it is fixed with the solution mentioned previously in the thread.

---

### Post by Sylchat on 2010-08-13
I have the P7P55D as well and networking with the Realtek 8112L chipset is awful on both Windows 7 and Ubuntu 10.04. LAN transfer rate are limited to 1MB/s !!!
Other features work well.

---

### Post by Sylchat on 2010-08-17
For anyone finding this thread, here's the solution: doing a cold boot of my computer restored the Realtek 8112l chip, my network is fast again.

See [http://ubuntuforums.org/showthread.php?p=9723664](http://ubuntuforums.org/showthread.php?p=9723664)

---

### Post by aboud on 2010-08-24
one problem I am having with this board is the controller, after formating and zeroing the drive many times, the new formated disk will have 3 to 9 GB of used space, under windows it works fine. some one mentioned that this is controller problem, so the controller can't reconize all the disk.

---

