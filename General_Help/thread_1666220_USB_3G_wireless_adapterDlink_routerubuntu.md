---
title: "USB 3G wireless adapter/Dlink router/ubuntu"
date: 2011-01-13
forum: General Help
---

### Post by cptrohn on 2011-01-13
Ok, I am thinking of giving this a try,  I can get a USB 3G mobile broadband adapter fairly cheap and get unlimited downloads for a fairly good price $40 monthly USD.  I have a Dlink router that I used to use that has a USB connection for a sharepoint, for printers, storage etc.   I am wondering if can plug that USB 3G adapter into the router and use it as an internet connection from there.   I can't find anything definitive anywhere on the web so I am just wondering how I would go about doing this.  I think I remember reading a while back that this is very much possible.  I also wonder if I can set up the 3G adapter with ubuntu (ie is it browser based?) or if I would have to use a windows PC to get that done.  The device is sold by Virgin Mobile, but I believe it is a Novatel product.  The router is a Dlink dir628.

Anybody ever try this crazy little idea? LOL

---

### Post by Juvencio on 2011-01-13
What type of 3G modem is it you are looking at getting?
I know Huawei can be con-fig in ubuntu I use to have a E220 it worked great.

As far as I know you can't connect a USB modem to a router.
But I may be wrong not to sure.

If you get the modem why do you want to connect it to the router?

---

### Post by efflandt on 2011-01-13
I doubt if that will work unless you have a proper router that can do that.  Web search "mobile broadband router".

I have used USB mobile broadband directly on an Ubuntu laptop, but did not configure iptables for masquerading a LAN through it.

Read the fine print to see if unlimited refers to no download limit or just how often you can connect.  Many have a 5 GB/month soft download cap, which they may throttle your speed, enforce, or charge extra if you go over that.

---

### Post by cptrohn on 2011-01-13
OK, well how about this....

What if I got the 3G stick, and then set up my desktop as a wireless access point?  See the thing is I am moving to an area where there is isn't any broadband service available other than DSL (very SLOW DSL), satellite or Mobile broadband.   I seem to remember reading somewhere that this could be done?   Uh... either way I need to figure something out...  I just figured the USB adapter costs less than the Mifi router...  So since I am a student as well anything that can save money is a plus for me right at the moment...  I just want to be able to stream netflix through my Wii is all!! LOL

---

### Post by cptrohn on 2011-01-13
> **Juvencio said:**
> What type of 3G modem is it you are looking at getting?
I know Huawei can be con-fig in ubuntu I use to have a E220 it worked great.

As far as I know you can't connect a USB modem to a router.
But I may be wrong not to sure.

If you get the modem why do you want to connect it to the router?

Its from virgin mobile  [http://www.virginmobileusa.com/mobile-broadband/ovation-mc760.html](http://www.virginmobileusa.com/mobile-broadband/ovation-mc760.html)  I did some digging and found a post in their question/answer section that says it will work out of the box with ubuntu....  

Or would the MiFi just be a better option?

---

### Post by efflandt on 2011-01-13
See [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing) or web search "ubuntu internet connection sharing".  Or this makes it look very easy [https://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/](https://jeremy.visser.name/2009/03/24/simple-internet-connection-sharing-with-networkmanager/)

---

### Post by Juvencio on 2011-01-15
How to create access point ?
[http://ubuntuforums.org/showthread.php?t=640564](http://ubuntuforums.org/showthread.php?t=640564)

Sharing Internet Connection in Ubuntu
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

---

### Post by Juvencio on 2011-01-15
How to create access point ?
[http://ubuntuforums.org/showthread.php?t=640564](http://ubuntuforums.org/showthread.php?t=640564)

Sharing Internet Connection in Ubuntu
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

How To Set Up Internet Connection Sharing For Ubuntu
[http://www.webupd8.org/2009/02/ubuntu-internet-connection-sharing.html](http://www.webupd8.org/2009/02/ubuntu-internet-connection-sharing.html)

---

### Post by Juvencio on 2011-01-15
How to create access point ?
[http://ubuntuforums.org/showthread.php?t=640564](http://ubuntuforums.org/showthread.php?t=640564)

Sharing Internet Connection in Ubuntu
[http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html](http://www.ubuntugeek.com/sharing-internet-connection-in-ubuntu.html)

How To Set Up Internet Connection Sharing For Ubuntu
[http://www.webupd8.org/2009/02/ubuntu-internet-connection-sharing.html](http://www.webupd8.org/2009/02/ubuntu-internet-connection-sharing.html)

---

