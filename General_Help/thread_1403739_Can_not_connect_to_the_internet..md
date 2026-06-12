---
title: "Can not connect to the internet."
date: 2010-02-10
forum: General Help
---

### Post by trunkmonkeytoo on 2010-02-10
Before I removed Ubuntu from my computer, I could not connect to the internet. I would like to know how, because I wanted to be able to use Ubuntu as another OS in my computer, but if I can't get it online, then I won't even try. 

I have a cradelpoint wireless router, and it works while I am using any other OS or computer. But for some reason, Ubuntu doesn't want to connect to the internet through my wireless router. Thank you for your help in advance!

---

### Post by NightwishFan on 2010-02-10
This is a guide to help you fix wireless.
[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide)

You likely need restricted drivers your device.

---

### Post by trunkmonkeytoo on 2010-02-10
My problem is that Ubuntu is not recognizing that I have a wireless network. In Windows, it gives you a list of WiFi networks, and you can select one, put it the password, and you're good to go. With Ubuntu, I can't even find my WiFi network in the list (which is empty).

---

### Post by NightwishFan on 2010-02-10
That means a working driver is not loaded. Try to use the methods described in my link to find the name of the hardware and the appropriate driver. For example on Debian I need to install zd1211 firmware to use wireless.

---

### Post by trunkmonkeytoo on 2010-02-10
Am I supposed to install these into the Windows 7 OS on my computer?

---

### Post by FearfulJesuit on 2010-02-10
@TrunkMonkey

1. Did you even read the guide that Nightwish linked you to? If you did not, go read the guide.

2. Think hard about the question you asked.

3. Connect to the internet with an ethernet cable. Then go to System -> Administration -> Hardware Drivers. It should show you which wireless driver to install. 

Please google and try things on your own and read guides when someone finds them and links them for you. You make it really frustrating by spamming the forums with otherwise easy problems.

---

