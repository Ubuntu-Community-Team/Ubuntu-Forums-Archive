---
title: "Wireless"
date: 2010-01-16
forum: General Help
---

### Post by DesmondB on 2010-01-16
Hey,

I know you guys get a lot of wireless questions, but I'm finding it really hard to get a solution via any tutorial, so I hope someone can help me out. 

So, I just downloaded and installed Ubuntu 9.10 (I'm a complete newbie). Love everything so far but I'm trying to connect to the internet. I have the TP Link TL-WN620G Wireless USB Card. I tried checking out iwconfig, and it stated that there are no wireless extensions. So I'm assuming that I would have to download drivers in order to get everything started. I downloaded some Windows XP drivers because after doing some research, I found out apparently I can use NDISWrapper to use XP drivers in disguise. 

However, my problem is I can't seem to install or get NDISWrapper. I tried looking at various videos on youtube but I simply don't have that option anywhere. I've searched in Synaptic Package Manager and it does not even come up on the list. It's really frustrating.

Can someone please tell me how I can get NDISWrapper working? 

Thanks in advance! :D

---

### Post by CompyTheInsane on 2010-01-17
> **DesmondB said:**
> I've searched in Synaptic Package Manager and it does not even come up on the list.

You did not mention whether or not you tried the refresh button in Synaptic. Did you already try clicking Refresh? Try it if you haven't.

Once the package list is refreshed, look for the following packages:
ndisgtk, ndiswrapper-common, ndiswrapper-utils-1.9

Double-click on ndisgtk (Note that it will require the two other packages which will also be selected for installation) and then click apply.

---

### Post by lincoln32 on 2010-01-17
quick first step ubuntu will try to install a lot of win drivers for wifi cards but they are not installed on cd disk so may want to try a lan cable
then update and then check system-administration-hardware drivers and it will show yor the drivers and files to make it work then get back to us for more in depth testing

---

### Post by Crafty Kisses on 2010-01-17
You can install ndiswrapper by running the following:
```

apt-get update
apt-get install ndiswrapper-common
```
You always have the option to compile ndiswrapper from source, you can find ndiswrapper right **[here.]("http://sourceforge.net/projects/ndiswrapper/files/")** Hope this helps.

---

### Post by DesmondB on 2010-01-18
Sorry for the late reply!

The problem is guys, I can't connect wirelessly to the internet from ubuntu - which is why even if I refresh/reload, it won't work. I'll try to download it manually on my laptop from the above link and then get it on ubuntu. Thanks for the help, I'll report back on the situation.

Also I can't use LAN connection, unfortunately.

---

### Post by DesmondB on 2010-01-18
Hey guys, what am I supposed to do next?

I have the XP driver on ubuntu and I also have the ndiswrapper 1.55 thing on ubuntu - how do I go about with the setup and stuff? I don't see anything.

Thanks in advance!

---

### Post by bkratz on 2010-01-18
> **DesmondB said:**
> Hey guys, what am I supposed to do next?

I have the XP driver on ubuntu and I also have the ndiswrapper 1.55 thing on ubuntu - how do I go about with the setup and stuff? I don't see anything.

Thanks in advance!

wish I had seen this earlier, you could have gotten ndisgtk and the ndiswrapper files from the installation CD. ndisgtk makes the installation quick and easy adding the setup program to system -- administration---windows wireless drivers.  Actually it still isn't to late, you could add the installation disk as a software source and install ndisgtk (which also installs any dependencies.)


You could add the disk under system--administration--software sources and check the CD

---

### Post by DesmondB on 2010-01-18
> **bkratz said:**
> wish I had seen this earlier, you could have gotten ndisgtk and the ndiswrapper files from the installation CD. ndisgtk makes the installation quick and easy adding the setup program to system -- administration---windows wireless drivers.  Actually it still isn't to late, you could add the installation disk as a software source and install ndisgtk (which also installs any dependencies.)


You could add the disk under system--administration--software sources and check the CD
Hey thanks for the reply!

I actually don't have the installation CD. I downloaded and installed it on my Vista first and then rebooted and got on ubuntu. Is there a way I can download it from the net? I did a quick google for ndisgtk but there are multiple files and I'm not sure which one to download.

Thanks again.

---

### Post by bkratz on 2010-01-18
I think this may have what you want

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by DesmondB on 2010-01-18
After much attempt, it just isn't working for me. :(

Ah well, I guess I'll have to wait for an easier way in the future. Thanks for trying to help.

---

