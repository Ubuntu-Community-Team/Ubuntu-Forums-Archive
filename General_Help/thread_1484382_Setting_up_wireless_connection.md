---
title: "Setting up wireless connection"
date: 2010-05-15
forum: General Help
---

### Post by mclizardman24 on 2010-05-15
Hi, I am having some trouble setting up my wireless connection. I have a desktop version of ubuntu, and am trying to connect wirelessly to my modem, but it dosent even seem to be recognizing my wireless usb card. How do I get it to do that? Also, when I go to set up new wireless connection, it asks me for my ssid, mac address, mode, bssid, MTC, Wep index, authentication, ipv4 setting, and ipv6 settings. What the heck am I supposed to put in for those things? Thanks for the help.

---

### Post by Snow986 on 2010-05-16
1) Are you sure your modem is a wireless base station?
2)ssid is the name of the network
3) mac address is the hardware address of the computer.  You can find it by opening a terminal and typing 
```

ifconfig -a

```
4) mode is most likely g
5) The only other thing you will likely have to configure is authentication which will depend on the router.

---

### Post by mclizardman24 on 2010-05-16
> **Snow986 said:**
> 1) Are you sure your modem is a wireless base station?
2)ssid is the name of the network
3) mac address is the hardware address of the computer. You can find it by opening a terminal and typing 
```

ifconfig -a

```
4) mode is most likely g
5) The only other thing you will likely have to configure is authentication which will depend on the router.
  Yeah, I use wireless with it all the time with a laptop.

---

### Post by Snow986 on 2010-05-16
Ok, then you should be able to check the settings and just duplicate (everything but mac address) onto the new setup. :)

---

### Post by mclizardman24 on 2010-05-16
One problem, don't have lappy anymore. i could have worded my earlier post better...

---

### Post by Snow986 on 2010-05-16
Ok well the most important thing is SSID which is the name of your network.  If you remember this and the authentication type and password then you are fine.  If not, the most likely scenario will be hard resetting the router (with a pen and the little button on the back) and then it will be back to default with no password.  However if your wireless card is working it should pick up wireless networks.  What kind of card is it?

EDIT: To avoid double posting I'll stick with the other thread...

---

