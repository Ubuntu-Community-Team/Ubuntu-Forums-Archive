---
title: "Wireless gives 'device not ready' error always"
date: 2012-03-16
forum: General Help
---

### Post by Prawesome on 2012-03-16
Hi, ):P
Well,I set up dual-boot on my Dell Inspiron1545 with Windows 7 and my wireless works perfectly with it.But i cant use it in ubuntu,it never shows any networks for me,it says that device not ready always..Could anyone please help me? I am pretty new to ubuntu,so please bear with me

---

### Post by Known unknownZ on 2012-03-16
Assuming you've got the wireless drivers installed (should be an option to DL them somewhere near the wi-fi icon in the system tray if not),  go into Edit Connections then the Wireless tab under that.

Click 'Add' and manually input your network's SSID and password info (if applicable), then click 'Save...' and close. I get a full list of networks now but that's what I had to do initially when I was first setting up so maybe it'll help

---

### Post by Prawesome on 2012-03-16
> **Known unknownZ said:**
> Assuming you've got the wireless drivers installed (should be an option to DL them somewhere near the wi-fi icon in the system tray if not),  go into Edit Connections then the Wireless tab under that.

Click 'Add' and manually input your network's SSID and password info (if applicable), then click 'Save...' and close. I get a full list of networks now but that's what I had to do initially when I was first setting up so maybe it'll help

It wouldnt work,i was trying to setup hotspot in my laptop.The connection is actually supposed to appear in the list but it doesnt.. :(

---

### Post by MARP1961 on 2012-03-16
I think that you are probably missing firmware/drivers that are not included in the default install. Dells often have wifi cards made by Broadcom and these need the correct firmware/driver installed.

Firstly I would plug into the internet via an ethernet cable. This should give you an immediate internet connection on reboot. Then allow all updates to be applied. You may get a message from an application called 'Additional Drivers' to install a wifi driver. For some people, simply clicking on this and installing the recommended one works after a reboot. You may have to open up the Additional Drivers manually and check.

With my son's Dell Inspiron 6400 we installed the recommended STA driver but it still didn't work. After much reading and asking on these forums I did a fresh install to remove any traces of the failed driver and ignored **Additional Drivers** but searched **Synaptic Package Manager** for** B43 Firmware Installer**. I let this install, rebooted and the network manager instantly found my wifi router. Connection was just the simple matter of entering my WPA passkey.

---

### Post by Prawesome on 2012-03-29
> **MARP1961 said:**
> I think that you are probably missing firmware/drivers that are not included in the default install. Dells often have wifi cards made by Broadcom and these need the correct firmware/driver installed.

Firstly I would plug into the internet via an ethernet cable. This should give you an immediate internet connection on reboot. Then allow all updates to be applied. You may get a message from an application called 'Additional Drivers' to install a wifi driver. For some people, simply clicking on this and installing the recommended one works after a reboot. You may have to open up the Additional Drivers manually and check.

With my son's Dell Inspiron 6400 we installed the recommended STA driver but it still didn't work. After much reading and asking on these forums I did a fresh install to remove any traces of the failed driver and ignored **Additional Drivers** but searched **Synaptic Package Manager** for** B43 Firmware Installer**. I let this install, rebooted and the network manager instantly found my wifi router. Connection was just the simple matter of entering my WPA passkey.

I will try it later..thanks :D

---

