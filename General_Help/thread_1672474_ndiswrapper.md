---
title: "ndiswrapper"
date: 2011-01-20
forum: General Help
---

### Post by bondmatt on 2011-01-20
Edit: I used a usb to ethernet port adapter to gain internet access. I reinstalled 10.04LTS then upgraded everything with the handy internet connection. Installed ndiswrapper again and it worked fine.

I am trying to install a pcmia netgear wireless card (wg511) in xubuntu 10.04 on an ancient ibm laptop.
 
I used this guide:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing Windows driver](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper#Installing Windows driver)
 
I do not have an internet connection on the IBM - it doesnt even have an ethernet port - so installed any ndiswrapper packages I could find on the live cd.
 
The driver installation seems to have worked according to the guide. It is section 3.5 where the driver is loaded that I have a problem.
 
```
 sudo depmod -a 
``` nothing prints to the screen (good? bad?)
```
 sudo modprobe ndiswrapper 
``` FATAL: Module ndiswrapper not found
 
Edit: So I found this: [https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)
It is indicated that this is a known problem and the solution starts with installing build-essential so that ndiswrapper can be compiled (oh dear god).
I have never compiled anything and I would be less worried but I cant seem to install build-essential off my live cd. It seems like whenever packages have dependencies my computer will only get 1 and then claim to be unable to get more. If I write them down and get them one at a time I seem to be fine but then come the dependencies with dependencies...
 
 
I would really appreciate any assistance.
 
Thank you,
- Matt Bondy

---

