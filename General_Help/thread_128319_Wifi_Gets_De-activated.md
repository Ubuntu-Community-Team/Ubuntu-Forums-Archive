---
title: "Wifi Gets De-activated"
date: 2006-02-11
forum: General Help
---

### Post by aseem_mal on 2006-02-11
Hi. Every time I re-start my computer, and go to a web page, the web page opens, but within 30 seconds my internet access is gone. The Wireless card gets disabled. Then I have to go System > Administration > Networking, and click the "Activate" button next to my wireless adaptor. Then it works fine. But the next time I login, same thing happens again.

I have a Atheros madwifi, with WEP and DHCP.

Please help.:???:

---

### Post by SWAT on 2006-02-11
It's normal for a WLAN card to be disabled by default after boot, so that explains why you need to activate it, everytime you login. I always start my WLAN when my system is booted using my custom commands (including WEP/DHCP). Although I'm using ndiswrapper, it's always a good idea to post the brand/model of your WLAN card.

---

### Post by aseem_mal on 2006-02-11
[QUOTE=SWAT]It's normal for a WLAN card to be disabled by default after boot, so that explains why you need to activate it, everytime you login. I always start my WLAN when my system is booted using my custom commands (including WEP/DHCP). Although I'm using ndiswrapper, it's always a good idea to post the brand/model of your WLAN card.[/QUOTE]

Why should you have to re-activate your WLAN every time you re-boot? I don't get that.
My Wifi card brand/model is: Atheros / AR5212 802.11abg NIC

Any clues please?

---

### Post by jcl on 2006-02-11
I have intermittant problems with my WLAN that sounds like might mirror what you are seeing... my Linux box is ok but I have a wireless b laptop that joins my b/g network... it runs XP... sometimes it connects for about 30 seconds but then gets kicked off the network... if I let it sit for about 5 minutes it will reconnect by itself for 30 seconds and repeats the cycle... but if I catch it sometimes while it is connected and reboot upon reboot sometimes it connects and stays connected... I have no idea why it does this and I just live with it (but there is probably an explanation)... it is a linksys network and all of my linksys g devices work great... it's just this one b device that does this...

Anyway, my point is your problem may not be O/S related... could be device compatibility or firmware related... anything in your system logs give you clues? Does this box do the same thing in windows (if you can try that)?

Also, you may want to install something like kwifimanager so you can watch your connection and see what it's doing.

---

### Post by aseem_mal on 2006-02-12
Actually, in my case, it is a OS related problem. I have a dual boot - XP + Ubuntu.
I never face this issue on XP. It occurs on every re-boot into Ubuntu.

- A

---

