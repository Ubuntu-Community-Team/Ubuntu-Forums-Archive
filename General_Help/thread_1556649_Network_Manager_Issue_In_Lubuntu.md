---
title: "Network Manager Issue In Lubuntu"
date: 2010-08-19
forum: General Help
---

### Post by jcris on 2010-08-19
First off mad, mad, ultra mad props on Lubuntu!!! If I made a distro from scratch it would have been Lubuntu, cept I'm sure my theming would have been horrible. Now Ive installed on a couple of my Laptops, and even had a few friends convert, and for the most part everything is hunkus doris, cept one small issue thats keeping me from slapping it on my trusty laptop. I'm lost as to what the problem could be. Ive tried just about all I can think of, but I use sprint mobile broadband to connect to the net and then use Network Manager to share this connection with the laptops and Palmtops around the house. I can get my sprint modem to connect thats not a big problem the problem is now I cannot get the Auto Eth0 to connect to send out as a share. It just refuses to connect. Now this is not a Lubuntu problem at all Im sure its somehow a Lxde problem, as Mint Lxde, PeppermintOS, and  so on do the same thing, refusing to connect Auto Eth0 while Sprint is connected.  Any Gnome based distro this works flawless, as does Xfce distros, so Im sure this is somehow something within Lxde. Im sure its down to just "missing" a file or some stupid overlooked thing, but Ill be damed if I can figure it. Im hoping phillw see's this post and has an answer or a starting point to what to try next. Anyway any help or ideas is very much welcome and needed. Im stumped.

---

### Post by phillw on 2010-08-20
Hi, the unmanaged eth0 is a reported bug with installing (some) desktop systems on to the minimal installation (net-boot) method.  and not just applicable to Lubuntu. One of the guys on Lubuntu has two methods of working around the bug. They can be found at [Unmanaged Wired Network](https://wiki.ubuntu.com/Lubuntu/DocumentationHelp/MinimalInstall#Unmanaged Wired Network). Either one works, so take your pick. The details of the reported bug is also there.

Regards,

Phill.

---

### Post by jcris on 2010-08-20
Thank you very much Phill. I used fix #2. Now I can use Lubuntu on all my PC's.

---

### Post by DJonsson2008 on 2010-10-06
Neither of the solutions work for me and/or maybe I have another problem. Lubuntu on logon/reboot does not see the LAN or the Internet unless I drop to a terminal and type in sudo dhclient.

Is there anyway to get lubuntu to see the LAN and internet without running sudo dhclient in a terminal?

---

