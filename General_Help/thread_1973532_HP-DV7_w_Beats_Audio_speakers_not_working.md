---
title: "HP-DV7 w/ Beats Audio speakers not working"
date: 2012-05-04
forum: General Help
---

### Post by Sxynerd on 2012-05-04
I recently upgraded with a fresh install Ubuntu 12.04 on my HP DV7-6135dx w/ Beats Audio.

The DV7 has 4 speaker and one Sub-woofer. Currently only two speakers are working. 

Previously with 11.10 I fixed the problem by adding the line "options snd-hda-intel model=ref" to this file, "/etc/modprobe.d/alsa-base.conf" and then I would restart the PC.

When I attempted to use this fix with 12.04 I get no sound at all.





> There was no change after doing this.


aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: STAC92xx Analog [STAC92xx Analog]
Subdevices: 1/1
Subdevice #0: subdevice #0
card 0: PCH [HDA Intel PCH], device 3: HDMI 0 [HDMI 0]
Subdevices: 1/1
Subdevice #0: subdevice #0870, uzi, G36, USP9 Tactical, PS90, FN57, HiPower, FMAS



sudo apt-get install --reinstall libasound2
[sudo] password for wolvee: 
Reading package lists... Done
Building dependency tree 
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 427 kB of archives.
After this operation, 0 B of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise/main libasound2 amd64 1.0.25-1ubuntu10 [427 kB]
Fetched 427 kB in 1s (250 kB/s) 
(Reading database ... 168192 files and directories currently installed.)
Preparing to replace libasound2 1.0.25-1ubuntu10 (using .../libasound2_1.0.25-1ubuntu10_amd64.deb) ...
Unpacking replacement libasound2 ...
Setting up libasound2 (1.0.25-1ubuntu10) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place

---

### Post by Sxynerd on 2012-05-05
alsa-info-script 

[http://www.alsa-project.org/db/?f=233c8c44df66fd6deb7cfcacb2a32e4881bb3c68](http://www.alsa-project.org/db/?f=233c8c44df66fd6deb7cfcacb2a32e4881bb3c68)

---

### Post by howefield on 2012-05-05
Thread closed.

Duplicate here : [http://ubuntuforums.org/showthread.php?t=1970627](http://ubuntuforums.org/showthread.php?t=1970627)

---

