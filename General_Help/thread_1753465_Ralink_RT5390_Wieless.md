---
title: "Ralink RT5390 Wieless"
date: 2011-05-09
forum: General Help
---

### Post by doriean on 2011-05-09
Hello Everyone And Thanks So Much For Any And All Help You Can Provide...

I have a hp g62x laptop Ive installed ubuntu 11.04 to my hard drive ive gotten everything working except

The ralink wireless i have a rt5390 installed and i saw this posted on another forum


rpm -i rt5390sta-2.4.0.4-6.3.src.rpm  cd ~/rpmbuild/ tar xf SOURCES/2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO.tar.bz2  cd 2010_1216_RT5390_LinuxSTA_V2.4.0.4_WiFiBTCombo_DPO/ patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-config.patch  patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-convert-devicename-to-wlanX.patch  patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-gcc-warnings-x86_64.patch  patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-reduce_debug_output.patch  patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-remove-potential-conflicts-with-rt2860sta.patch  patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-return_nonvoid_function.patch  patch -p0 < ../SOURCES/rt5390sta-2.4.0.4-WPA-mixed.patch  mv RT2860STA.dat RT5390STA.dat sudo mkdir -p /etc/Wireless/RT5390STA sudo cp RT5390STA.dat /etc/Wireless/RT5390STA make sudo cp os/linux/rt5390sta.ko /lib/modules/2.6.38-8-generic/kernel/drivers/net/wireless/ sudo depmod sudo modprobe rt5390sta

but im too much of a noob to get it to work if you could please help me id appreciate it






thanks

---

