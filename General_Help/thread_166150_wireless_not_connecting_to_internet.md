---
title: "wireless not connecting to internet"
date: 2006-04-25
forum: General Help
---

### Post by pongu on 2006-04-25
i'm new to linux. with much help i got it working dual boot with xp as of yesterday. needless to say, i know very little about linux. i'm working on a compaq v2030us laptop with an Intel Pro/Wireless 2200 802.11B/G WLAN. specs can be found here:

[http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00248733&lc=en&jumpid=reg_R1002_USEN](http://h10025.www1.hp.com/ewfrf/wc/genericDocument?cc=us&docname=c00248733&lc=en&jumpid=reg_R1002_USEN)

i have a wireless network at home secured as WEP (128-bit). i've tried everything i know (which isn't much) and can't connect to the internet. the status icon indicates connectivity and activity but i can't ping anything. it also shows signal strength. i know my network is connected to the internet because my desktop is online now.

under the wireless properties i have the connection enabled, the correct network selected, hexadecimal selected, and the WEP key entered. i read somewhere to insert dashes after every four characters in the key. i tried it with and without dashes. my configuration is set to DHCP. i acquired the static ip info from my desktop and tried it in ubuntu but still no internet.

i have also tried connecting via ethernet cable and still couldn't connect to the internet. i believe it all has something to do with how i'm trying to configure my laptop wireless (and wired) connection for my home because my laptop connected at my workplace (i had help there). there should be no hardware conflict here. i've tried changing my network encryption to WEP 64-bit, 128-bit, WPA, and even open. couldn't figure out how to connect in any.

i'm sure someone will know what to do immediately and i've probably provided way too much info for this problem but i wanted to be thorough. i hope my inexperience doesn't complicate a resolution. i appreciate any assistance.

---

### Post by souki on 2006-04-26
can you see the wifi spot ?
```
iwlist eth0 scan
``` (replace eth0 with your)

---

### Post by 0MG on 2006-04-26
are you able to ping the gateway? (router)

what does iwconfig tell you? does it give you a link quality greater than 0?

---

### Post by pongu on 2006-04-26
[QUOTE=souki]can you see the wifi spot ?
```
iwlist eth0 scan
``` (replace eth0 with your)[/QUOTE]
note that i'm probably not going to be familiar with any commands you give me but i'll try what you suggest.
i did iwconfig and this is what i got: (retyped from laptop)

eth1 Scan completed:
Cell 01 - Address:  00:16:B6:1B:81:87
ESSID:"Pookie"
Protocol:IEEE 802.11bg
Mode:Master
Channel:6
Encryption key:on
Bit Rate:54 Mb/s
Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
Quality=79/100  Signal level=-50 dBm
Extra: Last beacon: 2635ms ago

---

### Post by pongu on 2006-04-26
[QUOTE=0MG]are you able to ping the gateway? (router)

what does iwconfig tell you? does it give you a link quality greater than 0?[/QUOTE]
it let me ping the default gateway. i also did iwconfig and got this:


lo      no wireless extensions.

eth0   no wireless extensions.

eth1   IEEE 802.11g  ESSID:"Pookie"
         Mode:Managed  Frequency:2.437 GHz  Access Point: 00:16:B6:1B:81:87
         Bit Rate-54 Mb/s   Tx-Power=20 dBm
         Retry limit:7   RTS thr:off   Fragment thr:off
         Power Management:off
         Link Quality=77/100   Signal level=-52 dBm   Noise level=-88 dBm
         Rx invalid nwid:0   Rx invalid crypt:0   Rx invalid frag:0
         Tx excessive retries:0   Invalid misc:0   Missed beacon:0

sit0    no wireless extensions.

---

### Post by souki on 2006-04-26
hey, your wifi is ok !
I think you are just missing the dns settings

can you post your /etc/resolv.conf ?

---

### Post by pongu on 2006-04-26
resolv.conf shows:

search ma.dl.cox.net
nameserver 68.1.208.30
nameserver 68.109.202.25
nameserver 68.1.18.25

these are the same as the dns settings on my system running windows.

---

### Post by souki on 2006-04-27
can you ping them (the nameservers) ?

can you post the output of these commands
```
nslookup google.com
```
```
route -n
```

---

### Post by pongu on 2006-04-27
first two of the nameservers pinged unreachable.  68.1.18.25 never responded.

nslookup google.com came back "connection timed out; no servers could be reached"

route -n gave me this (don't have a great way of posting this):
Kernel IP routing table
Destination	Gateway	    Genmask	      Flags  Metric  Ref  Use  Iface
192.168.1.0    0.0.0.0	      255.255.255.0   U	      0	        0    0     eth1
10.11.2.0	0.0.0.0	       255.255.255.0   U       0         0    0     eth0
0.0.0.0		 10.11.2.5     0.0.0.0	          UG	  0	    0	 0     eth0
0.0.0.0		 192.168.1.1  0.0.0.0	         UG	 0	   0	0     eth0

---

### Post by pongu on 2006-04-27
first two of the nameservers pinged unreachable.  68.1.18.25 never responded.

nslookup google.com came back "connection timed out; no servers could be reached"

route -n gave me this (don't have a great way of posting this):

Kernel IP routing table
Destination
192.168.1.0
10.11.2.0
0.0.0.0
0.0.0.0

Gateway
0.0.0.0
0.0.0.0
10.11.2.5
192.168.1.1

Genmask
255.255.255.0
255.255.255.0
0.0.0.0
0.0.0.0

Flags
U
U
UG
UG

Metric, Ref, Use
0
0
0
0

Iface
eth1
eth0
eth0
eth1

---

### Post by souki on 2006-04-27
the routes are not good,

first stop your network
```
sudo /etc/init.d/networking stop
sudo ifconfig eth0 down
sudo ifconfig eth1 down
```

then set up the wifi interface
I've supposed here that 192.168.1.1 is the gateway
```
sudo iwconfig eth1 essid **Pookie**
sudo iwconfig eth1 key restricted **your_key**
sudo iwconfig eth1 mode Managed
sudo iwconfig eth1 channel 6
sudo ifconfig eth1 **192.168.1.23** netmask 255.255.255.0 up
sudo route add default gw 192.168.1.1 eth1
```

---

### Post by pongu on 2006-04-27
when i try "sudo /etc/init.d/network stop" it tells me command not found. what am i doing wrong?

---

### Post by souki on 2006-04-27
sorry, it's /etc/init.d/networking

oh, and I've forget to put 'sudo' in front of each commands

---

### Post by pongu on 2006-04-27
glorious. i'm online. thank you very much for your assistance. i have much to learn.

---

### Post by souki on 2006-04-27
great! :)

I don't remember exactly how you can make this permanent (I'm on dapper now)
but you can set this in /etc/network/interfaces

I hope you will find a breezy user for that

---

