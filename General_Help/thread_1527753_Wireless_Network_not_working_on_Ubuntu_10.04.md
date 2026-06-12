---
title: "Wireless Network not working on Ubuntu 10.04"
date: 2010-07-09
forum: General Help
---

### Post by SitarHER0 on 2010-07-09
I have a Dell studio 1558 laptop, which I have just installed Ubuntu 10.04 32 bit on it with wubi (It runs windows 7 usually). All seems to be fine, apart from the wireless networking doesn't appear to work. I click on the wireless network icon in the top bar, and it says "wireless: disconnected" and "wierless networks: disconnected".

I am a complete newbie to linux/ubuntu, so quite a lot of help would be appreciated!!

---

### Post by bobcollard on 2010-07-09
> **SitarHER0 said:**
> I have a Dell studio 1558 laptop, which I have just installed Ubuntu 10.04 32 bit on it with wubi (It runs windows 7 usually). All seems to be fine, apart from the wireless networking doesn't appear to work. I click on the wireless network icon in the top bar, and it says "wireless: disconnected" and "wierless networks: disconnected".

I am a complete newbie to linux/ubuntu, so quite a lot of help would be appreciated!!
In the System menu find Hardware Drivers.  You will need an Ethernet connection to install one, possibly STA Driver.  Then you need to click on the Internet icon in your task bar to find the wifi connection.

---

### Post by SitarHER0 on 2010-07-10
> **bobcollard said:**
> In the System menu find Hardware Drivers.  You will need an Ethernet connection to install one, possibly STA Driver.

Do you know exactly which driver/drivers are required for a Dell wireless 1397 WLAN mini card?

---

### Post by SitarHER0 on 2010-07-10
I have installed the Broadcom STA proprietary wireless driver using hardware drivers like you said. When I first downloaded it, it worked, and network connections gave me a list of wireless networks to connect to. However, after I rebooted like it told me to, the driver has a green light next to it, but under wireless networks it says 'wireless is disabled.' I've tried removing the driver so I could reinstall it, but all I got was an error message saying : 'SystemError: Failed to lock /var/cache/apt/archives/lock"

---

### Post by SitarHER0 on 2010-07-10
This has been resolved after going through this: [http://ubuntuforums.org/showthread.php?t=112526](http://ubuntuforums.org/showthread.php?t=112526)
Thanks very much for the help!
EDIT: This did help, until I rebooted, and the wireless was disabled again. However, after looking through this thread, I can manually (and quite easily) enable the wireless after booting: [http://ubuntuforums.org/showthread.php?t=1513587](http://ubuntuforums.org/showthread.php?t=1513587)

---

### Post by p852pck on 2010-07-20
I first used wubi back at V8 or even 7 and all ran fine, But my old laptop crashed and  had to install from XP from scratch and then used Wubi. This laptop was 7 or 8 years oldAnd wireless had been working before. Downloaded wubi 10.04 and ran it seemed to go well but no wireless. Found many suggestions in forums but finally solved by connecting to a wired internet connection. 10.04 installed fine and even found a legacy wireless driver all automatically. entered the name of my wireless connection. Seems like wubi didn't like to install correctly on old laptop with legacy driver. Now all OK
Thanks to all for many tips. Hopes this helps others.

---

### Post by himbo on 2011-01-01
hey friends !
I have a Dell studio 1558 laptop and im using win7..my wireless  ''Dell Wireless 1397 WLAN Mini-Card'' dosen't find a network wich i was working with before..plz help me !!

---

### Post by bobcollard on 2011-01-01
> **himbo said:**
> hey friends !
I have a Dell studio 1558 laptop and im using win7..my wireless  ''Dell Wireless 1397 WLAN Mini-Card'' dosen't find a network wich i was working with before..plz help me !!
Suggest you start a new Post, this one is solved.

---

