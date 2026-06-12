---
title: "Noob needs help with Ubuntu!!"
date: 2011-03-05
forum: General Help
---

### Post by Itzmir_Heman on 2011-03-05
Hey guys...

I have been having this problem for a while now. It started since my dad upgraded the internet package which involved changing the wifi modem. After that happened the first thing that happened was the ability to go wifi at home. My laptop cant go wifi at home so I need to your a cable to connect myself to the internet.

That was the beginning, soon I realized that I cant update my ubuntu, use any chatting software abd downloading any software like Java, Audacity or Minecraft!

I tried to do the upgrade manually but this seems to be the popular result. I will copy and paste one of the result below.

W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2](http://archive.canonical.com/ubuntu/dists/karmic/partner/i18n/Translation-en_US.bz2)  Unable to connect to 219.93.178.162 3128:


Please do help me out as I tried to seek help with a bunch of mates and none can help me with it.

Cheers,
Itzmir Heman

---

### Post by Itzmir_Heman on 2011-03-05
Anyone? Please?! I am begging here because this is killing me!

---

### Post by seawolf167 on 2011-03-05
Welcome to the forums!

> **Itzmir_Heman said:**
> upgraded the internet package which involved changing the wifi modem

Just to make sure I understand correctly - you changed your internet package through your ISP which then required that they send you a new router/gateway? 

If that's the case, it sounds like you simply need to set up your router's wireless capabilities.

The way to access your routers configuration page to set it up is to  physically plug it in with an ethernet cable (from the router to your computer ), then find out what it's default IP address is.

After you plug it in to your computer, you can find it's IP address by  opening a terminal (Applications -> Accessories -> Terminal), and  typing the following command

```
route
```You'll get an output thats something like this:

```
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     *               255.255.255.0   U     1      0        0 eth1
link-local      *               255.255.0.0     U     1000   0        0 eth1
**default         *192.168.0.1*     0.0.0.0         UG    0      0        0 eth1**
```The part you are looking for is the "Gateway" column for the "default" row.

If you enter this into the address bar in Firefox you'll be able to setup your router.

In the above case, you'd enter

```
http://192.168.0.1
```into Firefox's address bar, hit enter,  and you'll have access to the config page. (your numbers will probably  be different - maybe like 192.168.1.1 or 10.1.10.1)

Once you have access to the router's config page, simply change to the Wireless section and turn it on, enter an SSID, passphrase, etc. and you're good to go.

---

### Post by coldraven on 2011-03-06
If your dad's modem has wi-fi then the passphrase is probably on a sticker on the modem.
If not it will be on a card that came with the package.
If the card has been lost then do as SeaWolf says.

---

### Post by Itzmir_Heman on 2011-03-19
Thanks Seawolf for the help! But it didnt really help me with anything and I did not get any numbers from it!

I typed in route in the Terminal and this came out!


Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     1      0        0 eth0
link-local      *               255.255.0.0     U     1000   0        0 eth0
default         dsldevice.domai 0.0.0.0         UG    0      0        0 eth0

No numbers in the default row!

---

### Post by seawolf167 on 2011-03-21
Try these two:

192.168.1.0
192.168.1.1

i.e., in the address bar

[http://192.168.1.0](http://192.168.1.0)

---

