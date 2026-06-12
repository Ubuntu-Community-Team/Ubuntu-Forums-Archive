---
title: "help with dial up connection"
date: 2006-03-29
forum: General Help
---

### Post by harys on 2006-03-29
hi, i use an hp pavilion 8000 with an integrated modem but i don't know to make it work in ubuntu 5.10. i went through system>administration>networking and there is a logo of a telephone with writing "modem is not active". could you please tell me how to activate it. thanks . harys

---

### Post by StefanoCole on 2006-03-30
Well, jump to this link: [http://linmodems.org/]("http://linmodems.org/")

and download the scanModem utility. Run it and check for the file: ModemData.txt which is generated. This file should contain info about your modem chipset and possibly about available drivers.
Check also this wiki: [https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialup%29]("https://wiki.ubuntu.com/DialupModemHowto?highlight=%28dialup%29")

Stefano

---

### Post by hajk on 2006-03-30
The System --> Administration --> Networking menu already shows a non-activated modem interface (ppp0?), so chances are that there is already a driver loaded and working. To find out, hit the Properties button and fill in the required data, also under DNS make sure to activate nameservers provided by ISP, and in the first menu using ppp0 as gateway. Then activate the interface -- if it works, then all your troubles are over. If not, then you might have to search for drivers as suggested in the previous post.

---

