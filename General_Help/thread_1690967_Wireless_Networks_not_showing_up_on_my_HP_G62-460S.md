---
title: "Wireless Networks not showing up on my HP G62-460SS"
date: 2011-02-19
forum: General Help
---

### Post by san000 on 2011-02-19
Hi everyone,

I'm having a few disappointments with my new laptop since I installed Ubuntu on it. 

The first problem I found is that it doesn't seem to detect my WIFI. When I select the networks icon, it only shows wired network and VPN connections. It is very strange to me that when I execute "rfkill list all", I see this:

0: hp-wwan: Wireless WAN
             Soft blocked: no
             Hard blocked: no


Wireless WAN??? WTH is this? :P:P

---

### Post by grahammechanical on 2011-02-19
First, it would have been better if you had posted this in the Networking and Wireless forum and not General help. May be a moderator will move the thread for you.

Second, LAN = Local Area Network. Which means computers at the same location networked together. WAN = Wide Area Network. Which means computers at locations all over the country networked by means of the Internet. By the way, Intranet means a WAN that works like the Internet but is not connected to the Internet.

So, Wireless WAN is what HP call what other people call wlan or wlan0 (wireless local area network 0). It is local because we are going from the computer to the modem/router which connects to the WAN or Internet

The wireless adapter on laptops needs to be switched on by a key press. If it was not switched on the list would read Hard blocked: yes. As it also reads Soft blocked: no, then the wireless adapter is not switched off in software.

The question is this, is the operating system recognizing your wireless adapter? Has it installed a driver for it? Do you see a Network Manager icon? Right and left click it and note what you see and do not see.

Go to System>Administration>Additional Drivers and see if you need to activate a special driver for your device. You will need to be connected to the modem/router by ethernet cable for this to work.

Regards.

---

