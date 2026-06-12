---
title: "stuck at 1024 by 768 with ati rv350 9600"
date: 2011-08-19
forum: General Help
---

### Post by sdowney717 on 2011-08-19
lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV350 [Mobility Radeon 9600 M10] [1002:4e50]
scott@scott-MS-7104:~$ 

so what to do, at boot, the LED syncmaster 731N monitor wants 1280 by 1024 but that option is not shown under monitors

this is all that is in xorg.cong

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection


this comes back with nothing
scott@scott-MS-7104:~$ sudo dpkg-reconfigure xserver-xorg
[sudo] password for scott: 
scott@scott-MS-7104:~$ sudo dpkg-reconfigure xserver-xorg
scott@scott-MS-7104:~$ 

tried this to no effect
[http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html](http://www.ubuntugeek.com/ubuntu-tiphow-to-removeinstall-and-reconfigure-xorg-without-reinstalling-ubuntu.html)

---

