---
title: "Internet Connection Issue . [ Immediate Help ]"
date: 2012-09-23
forum: General Help
---

### Post by ryan andrews on 2012-09-23
I installed Ubuntu 12.04 way long back back . But i used it for only two weeks .
**My major problems is connecting to internet .**
Problem Description : I am using Reliance Broadband Wire-line Connection .To connect to internet i need to enter Username and password  and then i have to connect to internet .
But when i use it Ubuntu , i am able to connect internet but i loose connection every 5 min .
I need to connect and disconnect several times using network  icon on right top corner .
My connection Details : [ from my windows 7 machine ]
Connection-specific DNS Suffix: reliancebroadband.co.in
Description: Realtek PCIe FE Family Controller
Physical Address: &#8206;00-E0-4C-00-46-BB
DHCP Enabled: Yes
IPv4 Address: 123.***.67.71
IPv4 Subnet Mask: 255.255.252.0
Lease Obtained: Monday, September 24, 2012 7:43:52 AM
Lease Expires: Monday, September 24, 2012 9:48:03 AM
IPv4 Default Gateway: 123.***.64.1
IPv4 DHCP Server: 10.9.243.84
IPv4 DNS Servers: 124.124.5.136, 124.124.5.135, 124.124.5.141, 124.124.5.140
IPv4 WINS Server: 
NetBIOS over Tcpip Enabled: Yes
:confused::confused:
Please somebody help !!

---

### Post by claracc on 2012-09-24
You can try to install wicd and configuring it as network-manager.

Once you are sure wicd manages your connection, you can stop network-manager ( sudo stop network-manager) and preventing it stsrts at the begining or uninstalling it (always after being sure wicd works)

In my case, I have:

00:19.0 Ethernet controller: Intel Corporation 82562GT 10/100 Network Connection (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

And network-manager constantly connects and disconnect the wifi, I have been using wicd for two years without any problem.

---

### Post by ryan andrews on 2012-10-29
WICD Fixed My Problem .
There are Two versions of WICD one is for wirelss and one is for Wired network 
in my case WICD for wired worked .
You can Download and install bot from Ubuntu software center . Just chose better one for you .



This fully solved my problem , i just installed it from ubuntu software center and restarted ubuntu .
And Thats all . 










[COLOR=White]
Internet connection on Ubuntu fixed , reliance internet connection problem solved ,
internet connection fixed [/COLOR]

---

