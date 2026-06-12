---
title: "A network configuration help!!!!"
date: 2009-09-05
forum: General Help
---

### Post by veda87 on 2009-09-05
I don't know whether this is the right place to post this question.... if wrong, sorry for that... 

Today i installed ubuntu-8.10 in my system... I have Windows operating system too.. 

I had no problem on installing ubuntu, but the problem was I am unable to access the internet...
I have my own static ip address but not a dynamic one... 

when I entered into ubuntu, firstly it started to attain the dynamic ip address from the network.. It failed.. so It prompted me ```
Network disconnected
```

So I configured my eth0 through system->preferences->network tools... and I edited Auto eth0, gave my ip, netmask, gateway and DNS also... 

Then I tried mozilla but no internet connection... So I rebooted my system... All my eth0 configurations were gone...**Why is it so... **

Then I created a new Wired Connection 1 and configured it...Then tried, but still no internet connected..

After reboot, it first prompts me like```
Network disconnected
``` after few seconds, It prompts me like ```
network connected to Wired Connection 1
```
Even after that internet is not getting connected...

Please help me with this... 

NOTE: My internet connection is working well in Windows...

---

### Post by bodhi.zazen on 2009-09-05
Wired or wireless connection ?

Please post your details, ip address, netmask, etc.

You *should* be able to open a terminal and enter:

```
sudo dhclient eth0
```

---

### Post by veda87 on 2009-09-06
its a wired connection....

ok... let me try doing it... If some problem.. I will come back...

---

### Post by Barafu Albino Cheetah on 2009-09-06
Uninstall away this Network manager - it never works properly. Edit a file called /etc/network/interfaces. 
Mine is ```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp

```
You need to replace dhcp with your ip. Google for more info.

---

### Post by veda87 on 2009-09-06
I did it... I refered this following link

[http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-set-a-static-ip-address-in-ubuntu-810-intrepid-ibex.html")

It came in handy...
 
Have a look at this... The first solution of that did the work... 
[http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/]("http://linhost.info/2008/11/how-to-set-a-static-ip-on-ubuntu-810/")

Thanks a lot...

---

