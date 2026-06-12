---
title: "Internet won't work anymore"
date: 2006-04-28
forum: General Help
---

### Post by Gaia on 2006-04-28
Hi,

My Internet was working fine for the first while that I was using Ubuntu and now it won't work at all, everything comes up "Server Not Found" when i try to go to a webpage.

I dont understand as it's working fine in Windows....is there some command i can run to check my dns/ip and to maybe refresh it, or is something else wrong? Must be a Ubuntu setting because the Internet is working fine in windows.

Thanks.

---

### Post by oakz on 2006-04-28
Go the following menu to configure/restart your network interfaces: System -> Administration -> Networking. From here you can configure your interfaces, as well as deactivate and reactivate the interface that is giving you problems.

---

### Post by xgrendel on 2006-04-28
Another way you can view your network settings is by opening a terminal window and type:

~$ ifconfig

You can scan through the settings of your network card. Check to make sure you have an IP address set there. Generally speaking, eth0 will be the default networking card. If you are using a wireless network card, you can type:

~$ iwconfig

...to see the settings of your wireless cards and connections

---

### Post by lostvicking on 2006-09-18
I got a similar issue with my network too: after each reboot i have to deactivate and reactivate my network interface. I'm sharing an internet connection with a win XP box that is acting as the DNS for me. Any suggestions? its really annoying having to deactivate and reactivate every time :(

---

