---
title: "WiFi, got connection, can't use internet"
date: 2006-03-22
forum: General Help
---

### Post by kaif on 2006-03-22
Hello everyone. Just started using Ubuntu last week and I'm loving it! So very close to totally switching from windows.

I have a bit of a problem though. My parents have set up a wireless network in their house. There's no encryption or anything on it either.

All the other computers that use it (running XP) can connect to it fine and use the internet. However, my poor old Linux laptop is having some issues.

Basically, I can see the network, get a signal, get it's name, everything. But it won't let me use the internet. Where am I going wrong?

Below is a screendump of what KWiFiManager picks up.

[[IMG]http://img137.imageshack.us/img137/1372/screenie7mp.png[/IMG]](http://imageshack.us)

This is most upsetting, please help me find a way round this. I really want to avoid installing windows again over one small problem.

Thanks guys!

---

### Post by SuperBOB on 2006-03-22
Hey,

It could be a number of things but I suspect it has something to do with the access points setup

How many clients does it support?
Is DHCP enabled on it? (if not you have to setup your IP/Subnet manually)
Is mac address restriction enabled? (if so you need to add yours to the list)

---

### Post by NetMatrix on 2006-03-22
I agree with bob, I think if you manually set the access point it will help.

That is to code in it's MAC address in the access point field.

---

### Post by mumushi on 2006-03-23
[QUOTE=kaif]Hello everyone. Just started using Ubuntu last week and I'm loving it! So very close to totally switching from windows.

I have a bit of a problem though. My parents have set up a wireless network in their house. There's no encryption or anything on it either.

All the other computers that use it (running XP) can connect to it fine and use the internet. However, my poor old Linux laptop is having some issues.

Basically, I can see the network, get a signal, get it's name, everything. But it won't let me use the internet. Where am I going wrong?

Below is a screendump of what KWiFiManager picks up.

[[IMG]http://img137.imageshack.us/img137/1372/screenie7mp.png[/IMG]](http://imageshack.us)

This is most upsetting, please help me find a way round this. I really want to avoid installing windows again over one small problem.

Thanks guys![/QUOTE]


I agree with them, manually check the aacess point and try experimenting on the local ip too. Good luck! ;)

---

### Post by kaif on 2006-03-23
Thanks guys, I'll give it a shot tonight. Thankfully I have admin rights on the router so I should be able to sort this out.

Sorry if this is a n00b question, but how do I work out what my MAC address is?

---

### Post by kaif on 2006-03-23
Hmm... There's no MAC address filtering, DCHP is definately on, and the router hasn't hit it's client limit (I can use the wireless from this laptop when I boot it in XP)

This is becoming more of a router issue than a problem with Ubuntu. I'll try looking into Belkin support.

Real shame, this setup works for all the XP machines on the network but not on Linux :(

Any other suggestions? Thanks.

---

### Post by Azrael on 2006-03-23
Have you manually altered any network settings since you installed Ubuntu?

For the sake of clarity, could you open a terminal and try these commands and paste their results back here?:

cat /etc/network/interfaces
tail -n 100 /var/log/daemon.log | grep DHCP
ifconfig
iwconfig

---

### Post by NetMatrix on 2006-03-23
You can find your MAC address by typing

```
ifconfig
```

this will give you a listing of all of your interfaces.  Find your wireless interface and look for HWaddr this is YOUR MAC address.

On your router you should be able to find the MAC address for the wireless access point.  You can enter that MAC address into the Access Point field in YOUR configuration on your wireless interface.  This will tell the card exactly where to look for the DHCP information.  

Are you running Ubuntu or Kunbuntu?  I had issues trying to set up wireless with Kubuntu.  Kubuntu did not grab gateway information dynamically (for whatever reason) using my wireless card.  I had to enter it manually.

Hope this helps.

---

### Post by kaif on 2006-03-23
Okay, got the MAC address of my router, but I don't actually know where to enter it :-? 

the network connections editor in system>administration doesn't give me options to enter a MAC addy anywhere. Where am I meant to enter these details?

Oh, and I'm using Ubuntu - Dapper Drake build (love the temp artwork on startup :p)

Thanks a lot for the help by the way guys, really nice community here :)

---

### Post by NetMatrix on 2006-03-24
You would enter the router's MAC in the access point field, which is usually a couple of levels deep in the GUI config tool.  You may have to hunt around a little.

---

