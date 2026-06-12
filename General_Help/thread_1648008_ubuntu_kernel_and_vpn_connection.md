---
title: "ubuntu kernel and vpn connection"
date: 2010-12-18
forum: General Help
---

### Post by bou3lam on 2010-12-18
hi 
im a total newb i have a strange issue :) i have a laptop asus with xp sp3 and i managed to install ubuntu some 2 or 3 months ago , i installed it without a cd or usb but with a tool which i forgot how its called , all was working fine and just yesterday when i did some upgrades to ubunto the grub got in error and was unable to load, the only command which grub was able to perform is LS  i was unable to load even the windows os, since my cd reader is broken and i dont have usb , i did a boot from LAN (connected to internet through a vpn) , and there were option to install ubuntu 9.0.4 kernel 2.26.(..)    i386 , i had no choice and i installed it, all is fine but i cant create a vpn connection, if someone know how to solve this please help :)
thanks

edit: with a tool which i forgot how its called  (just remembred it , universal usb installer :)
update : its sems i need to install some openvpn app :) but i cant since i cant connect to internet

---

### Post by bou3lam on 2010-12-21
anyone please ?

---

### Post by bou3lam on 2010-12-26
can someone please tell me how i can install openvpn , i downloaded it as tar.gz and under ubuntu there are no options about install when i right click it

---

### Post by vangop on 2010-12-26
Hi!
What kind of vpn you need?
If that's your ISP vpn, most likely this is pptp. In this case it is already installed by default. Open network manager->VPN tab->Add to create a connection.
If you need a cisco vpn, you need to install [vpnc]("http://ubuntu-answers.blogspot.com/2010/12/cisco-vpn-with-vpnc.html").

---

### Post by bou3lam on 2010-12-26
thanks for the reply Vangop , yes its pptp, when i go to Open network manager->VPN tab->Add to create a connection.  the button add is grey and non-clickeable i have tried to install openvpn and its gave me errors about lzo : 
LZO headers were not found
LZO library available from [http://www.oberhumer.com/opensource/lzo/](http://www.oberhumer.com/opensource/lzo/)
configure: error: Or try ./configure --disable-lzo

with ./configure --disable-lzo  i got another error with ssl headers 

downloaded and tried to install openssl and zlo without success (i download from xp installation and i restart to ubuntu)

---

### Post by vangop on 2010-12-27
I would recommend installing soft from ubuntu repos via synaptic rather than compiling.
On my system I have the following packages:
```
$ sudo dpkg -l |grep -i pptp
ii  network-manager-pptp                 0.8.1+git.20100810t192516.1e6db5a-0ubuntu1        network management framework (PPTP plugin)
ii  network-manager-pptp-gnome           0.8.1+git.20100810t192516.1e6db5a-0ubuntu1        network management framework (PPTP plugin, GNOME UI)
ii  pptp-linux                           1.7.2-5                                           Point-to-Point Tunneling Protocol (PPTP) Client

```
Try installing them and then it should be possible to add pptp vpn.

---

### Post by bou3lam on 2010-12-27
> **vangop said:**
> I would recommend installing soft from ubuntu repos via synaptic rather than compiling.
On my system I have the following packages:
```
$ sudo dpkg -l |grep -i pptp
ii  network-manager-pptp                 0.8.1+git.20100810t192516.1e6db5a-0ubuntu1        network management framework (PPTP plugin)
ii  network-manager-pptp-gnome           0.8.1+git.20100810t192516.1e6db5a-0ubuntu1        network management framework (PPTP plugin, GNOME UI)
ii  pptp-linux                           1.7.2-5                                           Point-to-Point Tunneling Protocol (PPTP) Client

```Try installing them and then it should be possible to add pptp vpn.
is those apps present or i need to download them ?

---

