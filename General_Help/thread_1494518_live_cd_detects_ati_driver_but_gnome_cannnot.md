---
title: "live cd detects ati driver but gnome cannnot"
date: 2010-05-27
forum: General Help
---

### Post by dogafin on 2010-05-27
livesession seems to find my ati card, but when I boot from the hard drive, no luck. xserver is running, i get no errors no nothing but a crappy resolution or whatever you call your desktop when you dont have the graphics on. 
i could do another fresh install but i hate to lose my mouse settings, i have a three button trackball mouse, i forgot how i enabled the scroll lock, it seemed easy when i did initially a while back but i cannot find it in the mouse settings. i did a fresh install on another harddrive and i could not for the life of me configure my mouse. BUT my ati drivers load just fine.

so im looking at a trade-off trying to fix this problem.

well something happened, i stumbled across a program called kleansweep, it seemed like a good idea at the time, tried to be 'careful' with it but i still managed to fudge my machine after letting it delete all the 'uneeded files'. as a result, gnome wasnt listed in the menu anymore, all i could do was get into xterm and ~/.session i had to delete .profile to fix it and that took me forever to stumble upon google! well.. back to my problem, i dont have graphics! and ubuntu looks like poop!

this is my only problem right now and if i cant fix it id hate to do a fresh install because of my mouse issue, it will drive me nuts configuring it as it did the other day when i put ubuntu in another drive and i cant scroll! so.. having all these said

please help!

[IMG]http://img.photobucket.com/albums/v102/_H_E_L_/Screenshot-HardwareDrivers.png?t=1274940084[/IMG]

see? nothing!

i tried probing with other things like reinstalling fglrx or purging drivers from it, then reinstalling ati-driver-installer-9-3-x86.x86_64.run which btw has this output
> Created directory fglrx-install.wmYxdy
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro

Removing temporary directory: fglrx-install.wmYxdy


i dont know what else to do so.. if anyone happens to drop by and know what to do, a bit of help would be greatly appreciated! thanks!

---

### Post by dogafin on 2010-05-27
i was able to install another driver with a better output > Created directory fglrx-install.rxh2ex
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.723....................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================
Detected configuration:
Architecture: i686 (32-bit)
X Server: X.Org 7.5
Removing temporary directory: fglrx-install.rxh2ex
dogafin@dogafin-desktop:~$ 

but still cant load compiz/or the system to detect the ati driver to activate. i really dont know whats going on anymore.

---

### Post by dogafin on 2010-05-27
[SOLVED] well kinda, i reinstalled ubuntu. thanks but no thanks again ubuntu forums.

---

### Post by Breeegz on 2010-07-03
```
Verifying archive integrity... All good.
Uncompressing ATI Proprietary Linux Driver-8.593...........................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................................
==================================================
 ATI Technologies Linux Driver Installer/Packager 
==================================================

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro

```

I'm getting the same thing on a very fresh install..  I never had mine working.

I'm running an ATI Radeon xPress 200m

bump..

---

### Post by iwayandeka on 2010-07-23
I also got the following error:

Error: ./default_policy.sh does not support version
default:v2:i686:lib::none:2.6.32-22-generic; make sure that the version is being
correctly set by --iscurrentdistro

Can u pls tell me how u fix it? Im using lucid lynx 10.4 with ATI Radeon X1300. Pls help coz Im a complete  noobs in linux.

---

### Post by Mark Phelps on 2010-07-23
> **iwayandeka said:**
> Can u pls tell me how u fix it? Im using lucid lynx 10.4 with ATI Radeon X1300. Pls help coz Im a complete  noobs in linux.

There are NO current ATI proprietary drivers for your card, or for the previous poster, that will run in current Ubuntu versions.

The only driver that will work was automatically installed when you installed the OS -- the open source driver.

So, quit trying to force the installation of an incompatible driver.  You'll only end up trashing your display in the process.

---

