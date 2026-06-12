---
title: "yet again another wireless prob.."
date: 2011-07-16
forum: General Help
---

### Post by moonsal on 2011-07-16
Alright fellas, got a LAME problem here.. See it everywhere and read tons on it but nothing seems to help... Just installed Xubuntu 10.04(old HP POS i threw together right quick) and can't seem to get my wireless (card > bridge) to connect to the router.. Havn't been around 'nix for YEARS and I mean YEARS, early 90s!!!! I'm back now and want to get in it again... Now my card is all good, lspci picks it up and have the name of my "interface" so what's is wrong?? Sorry for the EXTREME n00b ? but any advice is much appreciated!! Need to get her runnin'... Thnx

---

### Post by moonsal on 2011-07-16
Must be a pretty frowned upon ?.............. Sorry for the n00bness... Just a link to something I have yet tried would be good..

---

### Post by smellyman on 2011-07-16
does it see the networks and can't connect to them or you see nothing at all.

What kind of card is it?  Maybe you can post the lspci here?

---

### Post by moonsal on 2011-07-16
Sorry, running 2 dif. systems... [IMG]http://i51.tinypic.com/6fxbnn.jpg[/IMG]

 It sees the card just can't get it to connect to the "router".. I apologize for my lack of knowledge ya'll.... sudo nm-tool  reads that my driver is 8139too and state is disconnected (type: wired?) Card is RTL..

---

### Post by wildmanne39 on 2011-07-17
Hi run these commands in a terminal
```
sudo lshw -C network
```
```
lspci -nn
```
```
iwconfig
```
```
lsmod
```
and post the outcome  here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by garvinrick4 on 2011-07-17
moonsal are you sure the Skunk wants to Live in that Mess.

---

### Post by moonsal on 2011-07-17
Here's the readout.. Had to type it in by hand though.... On a totally different sys... As for ol' stinky here, don't think he minds it..lol He helped create it..haha

sudo lshw -C network
```

description: Ethernet Interface
product: RTL-8139/8139C/8139C+
vendor: Realtek
phy. id: d
bus info: pci
name: eth0
vers.: 10

config: autoegotition=on broadcast=yes driver=8139too driver version=0.9.28 duplex= full latency=64 link=yes
yadad yada

```

lspci -nn
```

yada yada

01:0d.0 Ethernet controller [0200]: Realtek Semiconductor co. RTL-8139/8139c/8139c+

```

iwconfig
```

lo      no wireless extensions.

eth0    no wireless extensions.

```



lsmod
```

yada yada

8139too    18545  0

yada yada

```

---

### Post by gandaran on 2011-07-17
no wireless device detected in the output! is it a usb adapter? post the output of 
```
lsusb
```
also the output of
```
rfkill list
```

---

### Post by moonsal on 2011-07-17
No not a usb adapter... Only usb is keyboard and mouse and linux foundation root hub.. 

and nothing at all shows up for rfkill list... Just returns to the prompt...

---

### Post by gandaran on 2011-07-17
> **moonsal said:**
> No not a usb adapter... Only usb is keyboard and mouse and linux foundation root hub.. 

and nothing at all shows up for rfkill list... Just returns to the prompt...
are you sure there is a wireless device at all? there was only a ethernet device detected in the "lspci" output, if there was a wireless device it would also show another networking controller device.
or is it a wireless pcmcia card?

---

### Post by moonsal on 2011-07-17
MMM, good point.... The card it's self isn't a wireless, it's connected to a wireless bridge... So how do I fix this thing?? Again guys I'm sorry for the lame problems and appreciate your help!! Thank you

---

### Post by wildmanne39 on 2011-07-17
> **moonsal said:**
> MMM, good point.... The card it's self isn't a wireless, it's connected to a wireless bridge... So how do I fix this thing?? Again guys I'm sorry for the lame problems and appreciate your help!! Thank you
Hi, that I am not sure about, hopefully someone will have the answer.

---

### Post by moonsal on 2011-07-17
anyone???

---

### Post by miasmablk on 2011-07-17
check your BIOS settings?

---

### Post by moonsal on 2011-07-17
BIOS ain't got nothing to do with it... Worked fine with winblow$

---

