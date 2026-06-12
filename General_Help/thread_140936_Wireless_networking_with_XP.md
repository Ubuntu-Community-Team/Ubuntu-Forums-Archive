---
title: "Wireless networking with XP?"
date: 2006-03-07
forum: General Help
---

### Post by slaging on 2006-03-07
Last weekend I visted my folks, and found they upgraded there home network to wireless. I have a notebook with wi-fi that works in any public hot-spot, yet I'm unable to connect to my family's network.
Where do I beging?
I'm a newbie for networking, so do I need to configure Samba or ndiswrapper?
Let me know - Thanks.
P.S. I'm able to connect to the home network with the 'old' wired method, but my Fathers jokes are not helpful. :-?

---

### Post by soonindallas on 2006-03-07
[QUOTE=slaging]Last weekend I visted my folks, and found they upgraded there home network to wireless. I have a notebook with wi-fi that works in any public hot-spot, yet I'm unable to connect to my family's network.
Where do I beging?
I'm a newbie for networking, so do I need to configure Samba or ndiswrapper?
Let me know - Thanks.
P.S. I'm able to connect to the home network with the 'old' wired method, but my Fathers jokes are not helpful. :-?[/QUOTE]

you only need samba if you want to share files with windows computers on the network.

to establish if you need ndiswrapper you need to give more info about your wifi chipset.

you will be able to browse the web and send email by connecting to the wireless AP which is probably a router also.

if all you have is a basic ubuntu install and gnome, go to System > Administration > Networking

select your wireless interface and activate it.

click 'properties' and you should see access point name(s) in 'network names'.

select the network, enter the WEP key if necessary, use DHCP unless you need static IP setup and you should be set!

---

### Post by irw on 2006-03-07
If you can already connect to public Wifi hot-spot, then you do not need ndiswrapper - your laptop is already set up for wifi.

What is your parents setup - WEP/WPA, broadcasting ESSID, allowing only recognised MAC addresses?

How did you try to connect / what errors did you receive / not receive?

You could try GTKWifi or network-manager - do they detect the network / give you any info?

---

### Post by slaging on 2006-03-13
Thanks for the replies.
Almost got everything working using a static address.
Most of the problems are with the wireless router. A build-in securty feature was blocking access untill I added myself as a network user.
Now I'm able to access files and serf the net, but when I log off the wireless the whole network crashes.  Everything from router to pc has to be restarted after the crash.
I've sent for help from the manfacture and hope to see a response by the end of the week.
 Here are some info.
Wireless network:
[WiFlyer]("http://www.alwaysonwireless.com/wiflyer.html")
[XP Pro]("http://www.microsoft.com/")

my notebook:
Compaq Presario v2000
Broadcom 802.11g
ndiswapper 1.10

---

