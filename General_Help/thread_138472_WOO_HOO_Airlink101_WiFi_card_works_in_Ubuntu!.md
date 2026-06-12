---
title: "WOO HOO Airlink101 WiFi card works in Ubuntu!"
date: 2006-03-02
forum: General Help
---

### Post by txwylde on 2006-03-02
To all of you out there who have issues with the Airlink101 card. It does not work in Ubuntu, so you need to use te NDISWRAPPER. I finally got it all up and running. The trick is to make sure you:

ln -s /usr/src/linux-<kernel-version> /lib/modules/VERSION/build

If things wont work, try sudo the commands. I finally got it up and running and it works like a champ. :) The WIKI for the NDISWRAPPER is wrong there are a few more steps you have to do to ensure everthing is set up like make sure you have GCC and the Kernal Headers. You can install them by doing an sudo apt-get install.


I came real close to grabbing the USB Dlink wifi adapter and throwing this one out the window. A little persitance will get your stuff set up. :)

---

