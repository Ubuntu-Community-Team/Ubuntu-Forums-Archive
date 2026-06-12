---
title: "Wireless drivers"
date: 2012-04-24
forum: General Help
---

### Post by layers on 2012-04-24
I recently installed the ath9k driver manually to stop the problem with most Linux distros, when the wireless just stops working when downloading something or streaming a video.

Now, I never lose the connection, but when I have to connect to the network, it takes 30 seconds to do so - before, it was for 2-3 seconds. And since I just followed steps without being familiar with modular loading/unloading, how can I check if the old driver is not fighting with the new one, and the everything is loaded properly?

---

### Post by techsupport on 2012-04-24
> **layers said:**
> I recently installed the ath9k driver manually to stop the problem with most Linux distros, when the wireless just stops working when downloading something or streaming a video.

Now, I never lose the connection, but when I have to connect to the network, it takes 30 seconds to do so - before, it was for 2-3 seconds. And since I just followed steps without being familiar with modular loading/unloading, how can I check if the old driver is not fighting with the new one, and the everything is loaded properly?

Just out of curiosity are you running a 32-bit version of Ubuntu and trying to install 64-bit windows drivers in Ndiswrapper? If the drivers you are installing are Windows 64-bit and you aren't using a 64-bit version of Ubuntu you are going to have lag. If it even runs at all.

---

### Post by layers on 2012-04-25
I am running 64bit. I installed this: [http://linuxwireless.org/en/users/Drivers/ath9k](http://linuxwireless.org/en/users/Drivers/ath9k)

---

