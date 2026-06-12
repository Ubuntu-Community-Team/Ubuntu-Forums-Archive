---
title: "Ubuntu 12.04 blinking screen on startup - lenovo ideacenter"
date: 2012-04-13
forum: General Help
---

### Post by djpemberton on 2012-04-13
I have a new Lenovo Ideacenter which I have set up to dual boot W7 and Ubuntu 12.04beta2. Everything seemed to install fine, but I haven't been able to get into Ubuntu yet. I select Ubuntu in Grub with no apparent issues. When it tries to get into the Ubuntu login I hear the short drum sound, but the screen is rapidly blinking with purple as the primary color and nothing else on the screen discernible. 

Any suggestions?

Graphics: ATI Radeon HD 6450 Graphics

---

### Post by Quackers on 2012-04-13
Did you select "try ubuntu" before you installed it, to see if it works with your hardware?
It maybe a graphics issue. Try the nomodeset boot option
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by ewz on 2012-04-13
Hello I have an E-machine with that same Graphics card, I had a bit of trouble with it after installing Ubuntu Beta 1.
It worked fine in Live mode using the free ATI driver, but when I installed Ubuntu I ticked the  install third party/non free codecs which installed proprietary ATI Driver, which I think had a bug in it at the time.

I was able to fix the problem  by booting into recovery mode, then selecting enable networking
when returned back to recovery mode options I selected drop to root shell prompt.
 
There I was able to type apt-get update apt-get upgrade after installing all the updates and rebooting the graphics worked fine.
Though as I said, I was using the Beta 1 version.

Hope this helps :)

---

### Post by djpemberton on 2012-04-13
I got it fixed. I forgot about the "nomodeset" option. Once I used that and tried to install the proprietary driver with Jockey and rebooted, everything was fine on that front. However, it claimed to have a problem installing the driver, and it still lists no proprietary drivers as activated in Jockey. Nevertheless, I am up and running.

---

