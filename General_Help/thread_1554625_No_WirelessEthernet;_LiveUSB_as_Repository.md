---
title: "No Wireless/Ethernet; LiveUSB as Repository?"
date: 2010-08-17
forum: General Help
---

### Post by ScarletWyvern on 2010-08-17
Today, I bought an Acer Aspire One D260. Originally, I had intended to install Crunchbang on it. I installed Crunchbang 9 to a LiveUSB and ran the machine. I learned that some things didn't work out of the box with Crunchbang on the D260, so I followed [this guide.]("http://crunchbanglinux.org/wiki/howto/aspireone") Unfortunately, the Kuki kernel headers wouldn't install, since it wanted libqt3 as a dependency, but libqt4 was installed. I had heard Crunchbang was supposed to work out of the box, however, so I downloaded Crunchbang 10 Alpha. That had the same problem.

My mother recently bought the same model netbook, and I convinced her to use Ubuntu Netbook Edition in a dual boot. That worked flawlessly. I decided to install it on mine, too. Upon loading up the LiveUSB of UBN, no wireless. Though, I didn't remember having to use any restricted drivers for her netbook, I tried to install the Broadcom drivers. I had no Internet connection. I tried to connect via ethernet. Nothing happened.

In terms of the Ethernet controller, Network controller, and all the other commands, my output is that same as [this user's]("http://swiss.ubuntuforums.org/showthread.php?t=1505697").

I'd love to implement that solution, but I can't compile the compat-wireless driver because I don't have gcc... And I can't install gcc because I have no connection, nor can I download the gcc source and compile it on the netbook because I have no C compiler.

Since I'm on a netbook, I don't have a CD drive, and I don't have an external USB CD drive.

Is there any way I can use this LiveUSB as a repository to install build-essential? Or is there any simpler way to solve my wifi/ethernet problem?

I'd really appreciate some help, or else I've wasted $350. I foolishly wiped Windows right away; I figured Linux would work fine, since it has on a netbook of the same model only weeks ago. Of course, wiping Windows voided my warranty.

---

