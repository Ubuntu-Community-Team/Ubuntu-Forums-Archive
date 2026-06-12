---
title: "Unable to access the internet"
date: 2010-11-21
forum: General Help
---

### Post by Bob Zenith on 2010-11-21
Hello,

I just installed Ubuntu 10.10 today on my laptop (I installed it alongside Windows 7).

My problem is that I'm unable to access the internet; actually, I'm unable to access any wireless connection at all. 

I'm using a Linksys Wireless-G Notebook Adapter (2.4 GHz) in my laptop. 

From what I've read, normally, many wireless cards are detected by Ubuntu automatically when you install it. However, this did not happen with my card. 

...So, I'm not really sure what to do in order to gain access to the internet. Any information or tips would be greatly appreciated! :)

Thanks

---

### Post by garvinrick4 on 2010-11-21
I just took one out of retirement in my case and plugged it into usb port and it found same
as internal intel card I use, found all routers in neighborhood. Cysco Lnksys g also so make sure you have wireless enabled.
Driver must be included in kernel because also running 10.10 right now. 
You have right clicked on applet and enabled?
right click edit connections and edit wireless?
what does this say: should be 3 trues
```
gksudo gedit /var/lib/NetworkManager/NetworkManager.state
```[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true

---

### Post by Bob Zenith on 2010-11-22
Yes, the code came back with three trues. But, alas, no internet connection :(

---

