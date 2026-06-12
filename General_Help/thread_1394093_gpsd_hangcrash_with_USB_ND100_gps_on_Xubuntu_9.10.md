---
title: "gpsd hang/crash with USB ND100 gps on Xubuntu 9.10"
date: 2010-01-30
forum: General Help
---

### Post by monkeyal on 2010-01-30
Hi, 

I am having problems getting a ND-100 usb gps running without gpsd randomly going crazy.

The computer it is a Via Epia NX15000G with 1g ram and a lilliput touchscreen monitor running Xubuntu 9.10.

The GPS works initially and have had it working with xgps, navit and mapfactor navigator 9 through wine, however gpsd will randomly go crazy and takes around 96% of the CPU processor up according to the CPU monitor. While it is going crazy xubuntu slows to a snails pace and the gps doesnt work, the only way I have found to stop this is to sudo killall gpsd. I have not yet found whether the crash is triggered by anything as I had the computer running for over 2 hours yesterday with no crash, then I tried it again this morning and gpsd crashed within 5 minutes, no gps software was running other than gpsd. 

I have tried gpsd with -b and -N parameters and have also updated the ND100 GPS firmware to the latest version and it still crashes. The GPS works fine in Windows with no issues, so I presume its a gpsd issue in xubuntu.

Any ideas as to what could be causing this problem. Unfortunately I am fairly new to linux so don't know what else to try now.

Thanks

---

