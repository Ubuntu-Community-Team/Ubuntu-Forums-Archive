---
title: "Wireless troubles..."
date: 2006-02-05
forum: General Help
---

### Post by Nightmare JG on 2006-02-05
I'm having trouble getting my wireless card working on a laptop I recently got.
It's a Toshiba Satillite 330CDS, it using one of the AMDtek ADM8211 based cards.
The driver loads alright, and it's picked up as eth0, it seems to be configure alright, but It won't pick up a signal. dhclient can't find a connection either.

help?

---

### Post by nanotube on 2006-02-05
try running "iwlist eth0 scan" from the terminal, to see if it is picking up any networks? try also running "iwconfig" to see if your interface shows up properly?

---

### Post by X-Cannon on 2006-02-05
if you have the router on a WEP or WAP check that you have the right ssid and PW that is most likley the problem.

---

### Post by Nightmare JG on 2006-02-05
Well, iwlist didn't find anything, and iwconfig shows eth0, but everything is either off or 0, including acsess point.
The only thing that looksright to me is the ESSID, which is correct.

---

### Post by HokeyFry on 2006-02-05
go thru this guide:

[http://www.ubuntuforums.org/showthread.php?t=98709]("http://www.ubuntuforums.org/showthread.php?t=98709")

---

### Post by Nightmare JG on 2006-02-06
I installed the driver like you said but I have no idea how to change the driver that my card is using...

---

### Post by Nightmare JG on 2006-02-06
Well, I got my card to stop using the adm8511 driver, but it won't use the ndiswrapper.
It still shows up if I use lshw, adn it says it has no driver.
ndiswrapper says the driver and hardware are both present and working, but the card doesn't show up in the network manager.

---

