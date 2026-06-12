---
title: "My first Ubuntu - cannot access internet."
date: 2010-08-11
forum: General Help
---

### Post by QuickSnail on 2010-08-11
Hi all.

My first shot at Ubuntu is turning sour.  Help me plz. :(

Toshiba satelite A120 worked fine on XP via inbuilt network card over to my wireless modem /router.

I wiped xp and installed ubuntu alone.  But no net.  Everything I've tried has turned pear shaped.  "Searching" hasn't helped. 

Can u guys guide me thru this hiccup plz?

---

### Post by Quackers on 2010-08-12
Which wireless adaptor are you using?

---

### Post by azmo35 on 2010-08-12
Assuming that you have the "WLAN Atheros Driver" maybe you want try this 
> use the proprietary drivers for the Broadcom wireless cards. This can be done by going under System -> Administration -> Hardware Drivers and enabling the Broadcom B43 Legacy Driverand them update system > Update the System:

Open System -> Administration -> Update Manager

Update Apt:

Open the terminal then type in: sudo apt-get update

Update Synaptic:

Open System -> Administration -> Synaptic Package Manager then click "Reload" in the upper-right coner.for more detail see this page [http://www.associatedcontent.com/article/1753452/how_to_get_wireless_working_with_ubuntu_pg2.html?cat=15]("http://www.associatedcontent.com/article/1753452/how_to_get_wireless_working_with_ubuntu_pg2.html?cat=15")maybe this help you.

---

