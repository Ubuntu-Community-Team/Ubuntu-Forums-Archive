---
title: "How to connect to network from command line"
date: 2011-12-07
forum: General Help
---

### Post by rng on 2011-12-07
In ubuntu top panel, on the right side, there is an indicator showing network status. I click on that and choose the network option (which has ip address, gateway etc) and it connects. 

Can I do the same thing from command line? 

Thanks for your help.

---

### Post by josephmills on 2011-12-07
Yes you can there if using a ethernet just run ```
dhclient
```
wireless 
```
auto wlan0
iface wlan0 inet dhcp
wireless-essid   MYNETWOTK
wireless-key     FEFEFEFEFE
wireless-channel 11
wireless-mode    managed

```
 



here is link to learn more :) [https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

---

### Post by rng on 2011-12-07
I am using ethernet. I want to connect to internet using the values of ip address, netmask and broadcast that I have. How can I feed in these values with the command 'dhclient' ?

---

### Post by josephmills on 2011-12-07
dhclient does the work for ya if you are on a DHCP Client. 
Here is a link for that 
[https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html](https://help.ubuntu.com/10.04/serverguide/C/network-configuration.html)

---

