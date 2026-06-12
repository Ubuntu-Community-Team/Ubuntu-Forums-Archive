---
title: "My router thinks my laptop is IP spoofing. Help please"
date: 2012-07-27
forum: General Help
---

### Post by deaddevils1 on 2012-07-27
Every time I try to connect to the wireless my router shows that my ip is being spoofed. Am I being hacked or what is the issue? How can I fix this issue?

---

### Post by daslinkard on 2012-07-27
What about trying to set up a VPN so your computer doesn't look like it's trying to connect from a small foreign country?

---

### Post by Nixarter on 2012-07-27
> **deaddevils1 said:**
> Every time I try to connect to the wireless my router shows that my ip is being spoofed. Am I being hacked or what is the issue? How can I fix this issue?

What makes you think that your router has reached that conclusion?

---

### Post by papibe on 2012-07-27
Hi deaddevils1. Welcome to the forums ):P

Does your laptop have a static LAN IP?

Does other machine in your network have an static LAN IP?

Are those IP addresses outside  your router's DHCP range?

Regards.

---

### Post by deaddevils1 on 2012-07-27
my firewall logs on the router page says connection dropped ip "(ip address) " is spoofing to "(ip address)"

---

### Post by deaddevils1 on 2012-07-27
my network on the main desktop is setup to have a static ip not so sure about the laptop

---

### Post by deaddevils1 on 2012-07-27
> **daslinkard said:**
> What about trying to set up a VPN so your computer doesn't look like it's trying to connect from a small foreign country?

whats VPN and how do u set that up?

---

### Post by efflandt on 2012-07-27
Router firewall logs usually only log what they block from their WAN.  Many routers do not do loopback (LAN2LAN via WAN IP).

Do you by any chance have an application that is trying to connect to your LAN using your public IP or its DNS name?  Is the "(ip address)" the same IP in both cases?

---

### Post by Nixarter on 2012-07-27
> **deaddevils1 said:**
> my network on the main desktop is setup to have a static ip not so sure about the laptop


That is the problem.  It's probably like 192.168.x.x is spoofing to something, where the first IP is what it is trying to address the computer as, yet the computer is set up with a static IP and is basically saying, nope, I'm this other IP.

The solution is to go into your network settings and have it set to get its local IP from the network.  It basically puts it onto auto mode, and the static options become grayed out.  It should then ask the network for its IP, and then use the one it is assigned, and you are good to go.

---

### Post by daslinkard on 2012-07-27
VPN stands for Virtual Private Network (VPN) and allows you to set up a secured connection over a non-secured Internet connection....check out this link [here]("https://wiki.ubuntu.com/VPN").

---

### Post by deaddevils1 on 2012-07-27
> **daslinkard said:**
> What about trying to set up a VPN so your computer doesn't look like it's trying to connect from a small foreign country?

> **efflandt said:**
> Router firewall logs usually only log what they block from their WAN.  Many routers do not do loopback (LAN2LAN via WAN IP).

Do you by any chance have an application that is trying to connect to your LAN using your public IP or its DNS name?  Is the "(ip address)" the same IP in both cases?

not that im aware of but the ip's are different it says it spoofs from one to a totally different one

Jul 27 16:52:55 2012 Ip Spoofing from IP [my ip] to IP [unknown ip] dropped, umm on the unknown ip the last digits are .255.255

---

### Post by Nixarter on 2012-07-27
*.255.255 IP's are almost certainly part of a network mask.  Setting it to have the router assign it an IP address should still fix the problem.

---

### Post by deaddevils1 on 2012-07-27
> **Nixarter said:**
> *.255.255 IP's are almost certainly part of a network mask.  Setting it to have the router assign it an IP address should still fix the problem.

where in the router do i do that not sure how to go about actually doing that never done it before hehe

---

### Post by Nixarter on 2012-07-27
The router does everything automatically.  You have to adjust it on the device with which you are trying to connect to the internet (computer, laptop, or whatever).

In 12.04, right-cick on the network button (the up/down arows), and then click edit connections at the bottom.  Select your connection, then go to IPv4 settings, and change the "method" to automatic (DHCP).  Then save it and restart, then it should work.

---

### Post by deaddevils1 on 2012-07-27
> **Nixarter said:**
> The router does everything automatically.  You have to adjust it on the device with which you are trying to connect to the internet (computer, laptop, or whatever).

In 12.04, right-cick on the network button (the up/down arows), and then click edit connections at the bottom.  Select your connection, then go to IPv4 settings, and change the "method" to automatic (DHCP).  Then save it and restart, then it should work.

ok so i hav automatic dhcp already and umm it still says unidentified network not sure how to identify it

---

### Post by miegiel on 2012-07-27
> **deaddevils1 said:**
> i dont have 12.04 =S so how can i do it without it?

If you don't have 12.04, what do you have (and is it ubuntu or one of the other 'buntu flavors)? Usually there is a networking icon in your system tray. Left/right click it and choose something like configure/options/settings (just guessing ;)). DHCP is often listed under the IP4 tab.
> **deaddevils1 said:**
> ok so i hav automatic dhcp already and umm it still says unidentified network not sure how to identify it

Hmmm, OK ... [https://duckduckgo.com/?q=ubuntu+%22unidentified+network%22](https://duckduckgo.com/?q=ubuntu+%22unidentified+network%22) has a lot of windows results :S you're not running windows are you?

---

### Post by deaddevils1 on 2012-07-28
> **miegiel said:**
> If you don't have 12.04, what do you have (and is it ubuntu or one of the other 'buntu flavors)? Usually there is a networking icon in your system tray. Left/right click it and choose something like configure/options/settings (just guessing ;)). DHCP is often listed under the IP4 tab.


Hmmm, OK ... [https://duckduckgo.com/?q=ubuntu+%22unidentified+network%22](https://duckduckgo.com/?q=ubuntu+%22unidentified+network%22) has a lot of windows results :S you're not running windows are you?

ok so i dnt hav an unidentified network anymore but i still hav no internet access

---

### Post by miegiel on 2012-07-28
> **deaddevils1 said:**
> ok so i dnt hav an unidentified network anymore but i still hav no internet access

*"no internet access"* can mean a lot of things.

Can you do :
```
ping ping.xs4all.nl
```
or
```
ping 194.109.21.66
```

If the 2nd works but the 1st doesn't, than you have internet but need to configure DNS.

---

### Post by deaddevils1 on 2012-07-28
> **miegiel said:**
> *"no internet access"* can mean a lot of things.

Can you do :
```
ping ping.xs4all.nl
```
or
```
ping 194.109.21.66
```

If the 2nd works but the 1st doesn't, than you have internet but need to configure DNS.

first one said ping request could not find host ping.xs4all.nl. please check the name and try again

second one said ping statistics for some weird letters:
packets: sent=4, recieved=0, lost =4(100% loss)

---

### Post by miegiel on 2012-07-28
> **deaddevils1 said:**
> first one said ping request could not find host ping.xs4all.nl. please check the name and try again

second one said ping statistics for some weird letters:
packets: sent=4, recieved=0, lost =4(100% loss)

Assuming you can ping your router/modem. Your machine doesn't know it's way to the internet. You either need to configure DHCP on your modem, so that it tells the machine's it gives an IP address what the gateway IP address is. Or you need to manually set it on you PC. (router/modem/gateway are all the same machine in your case).

---

