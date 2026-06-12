---
title: "Wlan nic"
date: 2010-02-06
forum: General Help
---

### Post by altjx on 2010-02-06
I just left my home with my laptop and I realized linux doesnt like my wireless nic. So now I'm using an ethernet cable temporarily until I can try to figure this out. Anyways... 
There's two hardware drivers listed... There's

Broadcom B43 wireless driver
Broadcom STA wireless driver

Currently, the first one is enabled, but I get no wireless networks found in wicd network manager. I've tried disabling that one and enabling the STA one, still the same thing. I've tried disabling them both and installing "bcmwl-kernel-source" and restarted, still no wireless networks found.

Not sure what else there is to do =\. I'm sorta new with linux but I've learned a great amount within the past week. Any help would be much appreciated, thanks.
I have a Dell Wireless 1397 802.11g    Half Mini Card nic

once before when i had ubuntu 9.10 installed, it brought up the hardware drivers, and the minute i installed the first one, i was able to see other wireless networks. its not doing that this time and my wireless switch isnt turned off and there ARE wireless networks around

---

### Post by Pjotr123 on 2010-02-06
Make sure you have internet connection over the ethernet cable. Enable only the STA. Then do a reboot. 

Then remove the ethernet cable. Then click on the icon of Network Manager in the system tray (upper panel, on the right). You should see the available wireless networks.

Full story:
[http://sites.google.com/site/easylinuxtipsproject/internet#TOC-Broadcom-chipset](http://sites.google.com/site/easylinuxtipsproject/internet#TOC-Broadcom-chipset)

Good luck! :-)

---

### Post by altjx on 2010-02-06
> **Pjotr123 said:**
> Make sure you have internet connection over the ethernet cable. Enable only the STA. Then do a reboot. 

Then remove the ethernet cable. Then click on the icon of Network Manager in the system tray (upper panel, on the right). You should see the available wireless networks.

Gonna try that now, I'll post back with results. thanks

---

### Post by altjx on 2010-02-06
Just did what you said, still no wireless networks available. I've toggled the switch and I get the same results

---

### Post by altjx on 2010-02-28
Anyone? =\
I've installed t he bcmwl kernel source and rebooted, but whenever I try to activate the Broadcom STA driver, it gives an error, and shortly after the system crashes. This is a brand new installation

---

