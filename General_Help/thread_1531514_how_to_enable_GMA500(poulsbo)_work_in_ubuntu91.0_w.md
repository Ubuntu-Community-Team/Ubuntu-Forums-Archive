---
title: "how to enable GMA500(poulsbo) work in ubuntu91.0 with psb driver"
date: 2010-07-15
forum: General Help
---

### Post by junjinlee on 2010-07-15
Somebaody help.
my os: karmic memory: 512mb Cpu: atom z530 
lspci |grep VGA:00.02.0 VGA compatible controller: Inetl Corporation system Controller hub(SCH Poulsbo) Graphics Controller(rev 07)
I did fllow these steps:
 
sudo add-apt-repository ppa:gma500/ppa && sudo apt-get updatesudo apt-get install poulsbo-config poulsbo-driver-2d poulsbo-driver-3d psb-firmware psb-kernel-headers psb-kernel-sourceoulsbo-driver-3d psb-firmware psb-kernel-headers psb-kernel-source
 
sudo gedit /usr/bin/compiz
modify: WHITELIST="psb nvidia intel ati radeon i810 fglrx"
sudo gedit /etc/default/grub
 
sudo update-initramfs -u 
 
sudo gedit /etc/X11/xorg.conf
my xorg.conf:
 
Section "Device" 
Identifier "GMA500" 
Driver "psb" 
Option "AccelMethod" "EXA" 
Option "MigrationHeuristic" "greedy"
Option "IgnoreACPI" "true"
EndSection
 
Section "DRI"
Mode 0666
EndSection
[restart]
then cant't startx and happen a dialog:
Ubuntu is running In low-graphics mode(Title)
The fllowing error was encounted. You may need to update your configuration to slove this.
 
(EE)PSB(0):the stolenBase is: 0x1f800000
(EE)PSB(0):screenIndex is:0,fbPhys is:0x1f800000;
fbsize is:0x007df000
(EE)[drm] drmOpen failed.
(EE)PSB(0):[dri] DRIScreenInit failed.Disabline DRI.
(EE)[drm] Could not uninstall irq handler.
(EE) PSB(0): This driver currently needs DRM to operate.

---

