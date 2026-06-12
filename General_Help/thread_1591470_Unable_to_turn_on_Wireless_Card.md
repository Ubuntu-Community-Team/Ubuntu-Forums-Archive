---
title: "Unable to turn on Wireless Card"
date: 2010-10-09
forum: General Help
---

### Post by SedukiDude on 2010-10-09
I have installed Ubuntu via USB on a Dell Inspiron E1505 and I am unable to turn on the wireless card. I have a dual boot with Windows XP and I am able to turn on the card with keystroke Function/F2 and it works while in Windows. When I reboot in Ubuntu I am not able to use these keystrokes to turn on the card. Anyone with this experience? Thanx!

---

### Post by UnterUn on 2010-10-09
Hey! I had a similar problem on a different computer. Its a pain but if i remember correctly you have find and download Linux compatible drivers - In my case there were none so I had to used wired - But most do have the available drivers these days, best place to start if probably your wireless card's or routers website. - Good luck!

---

### Post by t4thfavor on 2010-10-09
Assuming the WIFI card is supported:

Boot into windows, turn it on, then boot into linux and see if it works. I had a similar issue with an HP, and I had to do that. The wifi button would work as long as the card was enabled when the os booted.

If not, find out what card you have (Probably Broadcom) then search for a broadcom wireless howto on the forums. G'luck.

---

### Post by SedukiDude on 2010-10-09
I booted into Windows, turned on the card, then rebooted in Ubuntu but the WiFi card will not turn on. I will check on downloading wirless drivers for Linux and try that. Thanx!

---

### Post by t4thfavor on 2010-10-09
Open a terminal, and execute the ifconfig command, and see if you have more than one adapter (one eth0, wlan0 or eth0, eth1) if you only have eth0, then your card is not supported out of the box. I know dell likes Broadcom, which is dificult to install at best. I.E the Dell 1309 is a broadcom card, while the Intel 2200BG is, you guessed it, Intel. Those are common cards for the dell you have.

---

