---
title: "Wireless network problems"
date: 2006-05-07
forum: General Help
---

### Post by SomaHoliday on 2006-05-07
I have ubuntu up and running finally after crashing my way through setting up the video card. Now I have another problem on my hands.

I use a Linksys internet network system. I have a Wireless USB Adapter to get the connection on windows but it doesn't seem to be accepting it on ubuntu. what could be the problem?

---

### Post by rowanparker on 2006-05-07
You will need to get the Linux drivers.

---

### Post by SomaHoliday on 2006-05-07
where might I get those from?

---

### Post by BitTorrentBuddha on 2006-05-07
Linux doesn't do so well with USB wireless adapters, I would recommend just throwing the .inf files that came with the windows drivers into that ndiswrapper gui. It's in automatix as Wifi something or another, you can find [automatix](http://ubuntuforums.org/showthread.php?t=138405) here.

---

### Post by dschaller on 2006-05-07
You have to make sure your wireless adapter's chipset is supported in Linux. The RaLink RT2500 chipset overall seems to be well supported. I have three different wireless cards using that chipset and they all work fine. The drivers are included in the Ubuntu Breezy kernel, it's autodetected, and you're off and running out of the box. My guess is you could have a hard time getting your linksys adapter going with Ubuntu. Something, for example, like the Zonet ZEW1601 [http://www.zonetusa.com/DispProduct.asp?ProductID=161](http://www.zonetusa.com/DispProduct.asp?ProductID=161) uses the RT2500 and should fire right up in Ubuntu with no hassles.

---

