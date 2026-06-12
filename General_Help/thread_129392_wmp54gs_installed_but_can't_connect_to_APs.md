---
title: "wmp54gs installed but can't connect to APs"
date: 2006-02-13
forum: General Help
---

### Post by IKoDiaKI on 2006-02-13
I've look through several forums and wiki's to try and figure out my problem, but im still a newb to linux. So far nothing has helped. I have a wmp54gs wireless card. I installed the driver, wmp54gs.inf, using ndiswrapper and all seemed to go well. My card showed up in the network configure menu and all the APs in my area are found by my card, so i know it is somewhat working. The problem is when i try to connect to any other AP, whether it is WEP encrypted or not. It simply wont connect. From the output of 
'iwconfig wlan0' it seems like the essid and ecryption key is not getting stored somewhere or something like that. I've tried using iwconfig to configure it and playing around with the /etc/network/interfaces file and nothing seems to help. I've been trying to fix this for 4 days now so if anyone could help it would be greatly appreciated. Thanks

---

### Post by IKoDiaKI on 2006-02-13
sorry i posted this in the wrong place on accident ... should i start a new thread in networking or just leave it here

---

### Post by RonJohnson on 2006-02-13
I had the exact same experience trying to set up a Broadcom card. After 3 days I gave up and purchased a new D-Link DWL-G630 vC2 which uses the Atheros chipset. I haven't had any problems and it was instantly recognized and installed by Breezy.  It's nice to now be able to use kismet so it was well worth the investment IMO.

Unfortunately I don't have any other advice, just my personal experiences.

---

