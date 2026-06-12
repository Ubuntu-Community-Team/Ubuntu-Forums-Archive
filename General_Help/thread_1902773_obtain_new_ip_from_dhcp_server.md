---
title: "obtain new ip from dhcp server"
date: 2011-12-31
forum: General Help
---

### Post by hg088 on 2011-12-31
ive tried this:
```
sudo dhclient -r && sudo dhclient
```
but i get the same ip

deleting the .leases file wont work

i read something about setting a preferred ip or something but i dont know how to do that

---

### Post by xyzzyman on 2011-12-31
DHCP server from your router or from your ISP?

---

### Post by hg088 on 2011-12-31
oh sorry, i should have clarified that

im connected directly to the modem, so im trying to get my isp to assign me a new public ip

---

### Post by xyzzyman on 2011-12-31
There isn't anything you can do on your end. Sometimes leaving it unplugged until the DHCP lease expires on their end but I've unplugged for a week while on vacation and wound up with the same IP when I came back.

---

### Post by hg088 on 2011-12-31
apparently the problem is that my isp associates my ip whit my mac and thats why i (and probably you) end up always getting the same ip

i guess that changing the mac would work, but, the weird thing is that i can get a new ip in windows xp without changing the mac with this script:

@echo off
ipconfig /release
netsh interface Ip set address "Wireless Network Connection" static 1.2.3.4 255.0.0.0 1.2.3.5 20
netsh interface ip set address name="Wireless Network Connection" source=dhcp
ipconfig /renew

so i guess there should be a way in ubuntu without that doesnt require changing the mac

---

### Post by xyzzyman on 2011-12-31
So you're not directly connected to the modem according to that script. You're wireless to the modem so it has a wireless router built in.

---

### Post by d3v1150m471c on 2011-12-31
dhcp sucks. configure your router to use static ip's and set your wicd(prefered), or network manager to the desired ip. some routers will allow you to set a static range so you can use static for your computers and dhcp for devices like phones and what not.

---

### Post by hg088 on 2011-12-31
you are right xyzzyman, im currently connected to a wireless access point but ive tried to do this also when connected to the modem via usb. actually, im in the windows xp partition right now and ive just use the script posted above to successfully change my public ip, but i cant find a way to do it in the ubuntu partition

---

### Post by xyzzyman on 2012-01-01
I've never seen an ISP wether it's cable, dsl or fiber that would issue a new IP address based off what's being done with those commands on windows. Every time someone shut off their computer and turned it back on they'd be getting a new IP address. Who are you using?

---

### Post by hg088 on 2012-01-01
i tried that commands in seven and it didnt work, but it did in xp

im from venezuela, its called cantv

happy new year by the way, and thanks for taking the time to answer me :D

---

### Post by vpharry on 2012-01-01
Try restarting the modem.... why do you need a separate ip?

---

### Post by hg088 on 2012-01-01
my main goal is to write a script that jdownloader can use to get a new ip so it wont stop downloads when limit is reached

---

### Post by xyzzyman on 2012-01-01
I have a feeling if you did those commands right now on an XP system you would have the same IP address still. Until you can try that there isn't much we can do for you. If by some reason you are able to reproduce it at the current time, then we'd have to research what exactly XP is sending differently that would allow that. 

According to wikipedia your service is DSL? Most likely your modem is logging in via PPPoE so your modem may actually be the one holding the lease not your computers.

---

### Post by hg088 on 2012-01-01
in my netbook with win xp i can get a new public ip by running the batch file i posted above. did it about 3 hours ago

on the same netbook in the ubuntu partition a run: sudo dhclient -r && sudo dhclient
but that wont get a new ip

im connected to a wireless access point and it is connected to the modem. all the devices that connect to the modem get public ip

i read some where that i had to set a preferred ip or something in order to get a different ip, otherwise the dhcp server will assign me the same one if the lease associated to my mac hasnt expired

im a bit of a noob, and dont really know what is PPPoE ^^

---

### Post by xyzzyman on 2012-01-01
> **hg088 said:**
> in my netbook with win xp i can get a new public ip by running the batch file i posted above. did it about 3 hours ago

on the same netbook in the ubuntu partition a run: sudo dhclient -r && sudo dhclient
but that wont get a new ip

im connected to a wireless access point and it is connected to the modem. all the devices that connect to the modem get public ip

i read some where that i had to set a preferred ip or something in order to get a different ip, otherwise the dhcp server will assign me the same one if the lease associated to my mac hasnt expired

im a bit of a noob, and dont really know what is PPPoE ^^

Can you give us the output of ifconfig then?

---

### Post by hg088 on 2012-01-01
ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:23:8b:3f:c5:59  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:44 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:112 errors:0 dropped:0 overruns:0 frame:0
          TX packets:112 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9504 (9.2 KiB)  TX bytes:9504 (9.2 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:09:b6:36  
          inet addr:190.75.202.231  Bcast:190.75.223.255  Mask:255.255.224.0
          inet6 addr: fe80::224:2bff:fe09:b636/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:26023 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21559 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29964046 (28.5 MiB)  TX bytes:3231898 (3.0 MiB)

```i ran the dhclient whith the -v to see its output
```

sudo dhclient -r -v:
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:24:2b:09:b6:36
Sending on   LPF/wlan0/00:24:2b:09:b6:36
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 200.109.126.43 port 67
Reloading /etc/samba/smb.conf: smbd only.
``````
sudo dhclient -v
Internet Systems Consortium DHCP Client 4.1.1-P1
Copyright 2004-2010 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan0/00:24:2b:09:b6:36
Sending on   LPF/wlan0/00:24:2b:09:b6:36
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 6
DHCPOFFER from 172.17.161.239
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 172.17.161.239
Reloading /etc/samba/smb.conf: smbd only.
bound to 190.75.202.231 -- renewal in 1581 seconds.

```

---

### Post by hg088 on 2012-01-01
when dhclient tries to release the lease the output says something about "Sending on   Socket/fallback"

is this normal?

---

### Post by hg088 on 2012-01-06
ive finally managed to find a way to get a new ip without changing my mac.
apparently  the trick was to ask the dhcp server for an specific ip and this forces  it to give me a different ip. dont really know why since im a total  noob [IMG]http://crunchbanglinux.org/forums/img/smilies/sad.png[/IMG]
this can be done using the send option in the dhcilent.conf file
so every time i want to get a new public ip i just have to run this bash script i made

```
sudo dhclient -r -v eth2 && sudo rm /var/lib/dhcp/* 
sleep 1
 sudo sh -c "echo 'interface \"eth2\" { send dhcp-requested-address 1.2.3.4;}' >> /etc/dhcp/dhclient.conf"
 sleep 1
 sudo dhclient -v eth2 &
 sleep 1
 sudo sed -i '$ d' /etc/dhcp/dhclient.conf
 sleep 3
 sudo killall dhclient
 sleep 6
 sudo dhclient -v eth2
```im happy i could work through this because, if windows xp could do it why the hell linux wasnt gonna be able to [IMG]http://crunchbanglinux.org/forums/img/smilies/big_smile.png[/IMG]

---

### Post by xyzzyman on 2012-01-07
You may have the only ISP that allows this. lol

---

### Post by hg088 on 2012-01-07
the only isp that allows changing the the ip without spoofing the mac?

---

