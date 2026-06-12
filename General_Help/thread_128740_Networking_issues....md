---
title: "Networking issues..."
date: 2006-02-12
forum: General Help
---

### Post by zoolfoos on 2006-02-12
I am trying to install Ubuntu 5.1 on a Sony Vaoi VGN-FS740.

Unfortunately, I have been getting a "debootstrap error" during the install of the base system from the Ubuntu DVD. Apparently many people are having a simlar problem which is attributed to only an error during the burning process of the DVD. At the moment I do not have access to a computer which can burn the DVD... except for the one that I am trying to install Ubuntu on.

I decided that, instead I would install directly form a mirror of the Ubuntu archive. Well... it seems that there is some sort of problem with the networking situation here. The computer has an Intell PRO/Wireless 2200BG card and a regular Intel 1068 wired ethernet card. Ubuntu can see both cards, but is unable to make a connection to the network. I have tried using a static IP instead of attempting to get a DHCP lease, but this did not help. It was not able to make a connection with the internet via wireless or wired connection. 

When I run the live DVD the local wireless network is available... but when I activate the wireless card it comes up as "disconnected". By the way, the local network has a DSL connection, I believe. This has made a difference in some cases (I think?).

Thanks!
-Kevin

---

### Post by njzillest on 2006-02-12
i have been experianceing the same problems and then i got it to work. Im using hte same cards. 


Are you picking up signals? is your card enabled? and what band router are you tring to connect to? are you using a WEP or a WPA internet security?

please answer these questions so i may help you

---

### Post by zoolfoos on 2006-02-12
Hi!

Thanks for replying!

My card is enabled and I must be picking up some signal, because, in the network config GUI in the Live version of Ubuntu, my local network is detected. Although, it says that it is recieving no signal.

The router is a 2.4 Ghz ISM-Band router using WEP security.

Thanks again!!
-Kevin

---

