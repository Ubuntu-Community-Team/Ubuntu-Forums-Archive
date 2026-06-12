---
title: "Help - How can i find/remove the last APT package? ATI Configurator kills screen"
date: 2009-08-22
forum: General Help
---

### Post by AstroPhysik on 2009-08-22
Hi togehter! 

yesterday i've installed an ATI Catalyst Control Center via - commandline: sudo get-apt... But now the Laptop screen freezes during booting. The usual system tasks are shown during booting but if ubuntu switches to the gnome desktop  i get 4 frozen ubuntu logos at the top of the screen...
I can access tha system via live-cd or recovery mode (root commandline)
Obvisous the ATI configurationprogram collides with the ubuntu graphics drivers..???
I did't had installed the proprietare 3D drivers from System/Hardwaredriver.

**My question:**
How can i find out at the root console which was the last package apt installed?
(because i forgot the detailled name of the ati configurator.. but it was tha last package i'd installed) And how can i remove it from APT in the command line?

**My Data:**
HP Pavilion dv5-1112ea Notebook,Processor: AMD Turion X2 Ultra Dual-Core Mobile, 2.2 Ghz &#8211; ZM82 with 2MB L2 Cache, Ubuntu 9.04 - 64 Bit (CD: ubuntu-9.04-desktop-amd64.iso ),ATI Radeon 3450, Kernel: Linux HPdv5-laptop 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 19:25:34 UTC 2009 x86_64 GNU/Linux, 
*ubuntu@ubuntu:~$ lspci | grep VGA* 
01:00.0 VGA compatible controller: ATI Technologies Inc Mobility Radeon HD 3400 Series

thanx AstroPhysik

---

### Post by geirha on 2009-08-22
/var/log/dpkg.log contains the log of installed and removed packages.
```
grep 'status installed' /var/log/dpkg.log
```

Then to remove the package
```
aptitude remove **packagename**
```

---

### Post by AstroPhysik on 2009-08-22
Hi geirha,
Thanx very much 4 the tip:

i think it was the ATI Catalyst Control Center i've installed.
*grep 'status installed' /var/log/dpkg.log*   showed:
[php]
man -db 2.5.5-1build1
dkms 2.0.21.1-0ubuntu3
fakeroot 1.12.1ubuntu1
fglrx-kernel-source 2:8.600-0ubuntu2
xorg-driver-fglrx 2:8.600-0ubuntu2
fglrx-amdcccle 2:8.600-0ubuntu2
libc6 2.9-4ubuntu6
[/php]It seems that te ATI catalyst contrlo center did install new fglrx drivers..
Do i need to do a new clean installation of my ATI Radeon drivers? (R600 is for ATI Radeon 3450)

vg. AP

---

### Post by philinux on 2009-08-22
Quick fix.

Boot into recovery and choose xfix. Then resume normal boot. That should get you back the default vesa driver and access to your desktop.

---

### Post by AstroPhysik on 2009-08-22
Hi,thanx  i've done this already, but it did'nt worked. Now i have a black screen without the 4 ubuntu emblemes..

---

### Post by Scott M. Sanders on 2009-08-22
Try this: [http://ubuntuforums.org/showthread.php?t=1056539](http://ubuntuforums.org/showthread.php?t=1056539)

---

### Post by AstroPhysik on 2009-08-22
Thank you so much, i had exact the same problem.
I was searching whole the day for a solution.  

I've * booted in recovery *mode as * root*, typed *aptitude*, in *installed/misc/binaries *i found the fglrx, i selected with ctrl+t in the Menue *Package/remove* only 
> 
fglrx-kernel-source 2:8.600-0ubuntu2
xorg-driver-fglrx 2:8.600-0ubuntu2
fglrx-amdcccle 2:8.600-0ubuntu2 
and kicked it out of my system with action / install-remove and it worked. 
(dkms seems to be needed for the linux-kernel-generic-drivers...i did not touch it!!!  *gg* )

I've read  [http://wiki.ubuntuusers.de/Grafikkarten/ATI](http://wiki.ubuntuusers.de/Grafikkarten/ATI) so i wanted to install the ATI Catalyst Control Center first, with hopes to see further information without changing anything (and not damaging anything..) . But it installed the fglrx drivers by itself and the screen went black...


 thanx a lot to all of you, AstroPhysik!!!  :popcorn:

---

### Post by AstroPhysik on 2009-08-22
How can i mark this thread as solved?

---

