---
title: "Kubuntu 10.10 with ATI Radeon 8700 issues"
date: 2010-10-24
forum: General Help
---

### Post by hailochild on 2010-10-24
I installed Kubuntu 10.10 as my host OS that uses a HD Radeon 4870 and am noticing some irregularities.  I started off not being able to use the "Desktop Effects" with a fresh install so considering that as a nice feature I went ahead and installed the restricted drivers.  When I look under Kinfocenter the 3D Accelerator is showing "unknown" while the ATI control panel seems to have all the correct information.  My dual screens both work correctly too but  when I drag a window the window border and title bar becomes "choppy" and slow.  The effects are disabled and if I re-enable them they become disabled again if I drag a window or do anything within the OS.  I have deleted my xorg.conf and recreated using aticonfg --initial.  I have googled online to find out that I should set the "openglisunsafe=false" in Kwinrc.  Then I even uninstalled all the ati drivers and I booted up into failsafe and downloaded the drivers straight from ati.com.  Followed the directions each step of the way which was fairly intuitive anyways but after restart same symptoms.  I must confess I am fairly new to KDE.  I normally have been a long time fan of Nvidia and have ran all my prior systems including my actual work machine on Nvidia cards.  This card though has been far superior to the others cards I have supported just because I am not a big gamer and they typically are in the $150-200 range.  Short story graphics are irritatingly not performing to par and I want my desktop effects. =) lol  I took a screen shot of the knifocenter but I think that is probably normal with the 3D accelerator and I will attach the log files if need be but there weren't any errors in the Xorg.0.conf.  Let me know if there is any recommendations or if you want me to upload and conf files.

:popcorn:

---

