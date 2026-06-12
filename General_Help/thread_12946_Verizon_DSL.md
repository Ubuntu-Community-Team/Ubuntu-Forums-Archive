---
title: "Verizon DSL"
date: 2005-01-27
forum: General Help
---

### Post by ElmerFishpaw on 2005-01-27
Hi Unbuntu users!
I have never used Linux. I'm trying various distros. I downloaded and burned Warty Warthog and I'm trying it out. I'm taking the big plunge before long and canning Windows. When I use the Live CD,  I type an address on the browser and I'm not connected. I use Verizon DSL..not on a wireless router. Is this locked out on the Live CD? If I do go with UBUNTU on my hard drive..will it unlock? Thanks in advance!

---

### Post by machiner on 2005-01-27
open a terminal...type:
sudo pppoeconf
then your password

follow the prompts (you'll hit enter a lot...your uname and password, more enter...

enjoy

---

### Post by ElmerFishpaw on 2005-01-27
Thanks Machiner......I got  a message saying my Ethernet card wasn't recognised...It asked if I wanted modconf? to start up and help with a driver...I entered "yes" and no luck....

---

### Post by greyspace1979 on 2005-01-28
Thanks Machiner

I logged onto this forum because I had the same problem with SBCYahoo DSL. I typed sudo pppoeconf in a terminal and I am now writing this from the Ubuntu LiveCD. Pretty cool.

G

---

### Post by machiner on 2005-01-28
[QUOTE=ElmerFishpaw]Thanks Machiner......I got  a message saying my Ethernet card wasn't recognised...It asked if I wanted modconf? to start up and help with a driver...I entered "yes" and no luck....[/QUOTE]


what NIC card are you using? Or - are you using a mobo with built-in LAN?

Nforce is wildly popular these days...you may have an nforce chip -- if so at the terminal type:
sudo modprobe forcedeth

after the driver is loaded then do the pppoeconf thing.

Of course there are a zillion other drivers -- so let's start with your NIC...

Let us know - you'll be zoomin' in no time.

---

### Post by ElmerFishpaw on 2005-01-29
Thanks Machiner!...No matter what I do, it won't recognise my Ethernet card. It's a Linksys np100-The live CD I'm using now is a knoppix distro which recognised my card as eth0-I have a common card and Verizon DSL is common...so I know I'm overlooking something very simple.

---

### Post by ElmerFishpaw on 2005-02-12
OK...problem fixed!!! All I did was buy a COMPUSA PCMCIA 10/100 Ethernet Notebook adapter 32 bit ($20) at CompUSA....pulled up the browser and boom...on the internet!!

---

