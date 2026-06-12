---
title: "Airlink awlh3025 Wi Fi problem"
date: 2006-02-21
forum: General Help
---

### Post by txwylde on 2006-02-21
I have installed Ubuntu, allowing it to take the updates via my ethernet card. I also wanted to make sure I had the source and NDISWRAPPER in case my Wi Fi card wasnt detected. I was surprised to see that it was. I have tried configuring my card in terminal as well as the network utilities. I enable the the wifi card and cant seem to get the network to connect. I have go into my router's settings to ensure i have the ESSID settings correct. Ironically, my card worked with NDISWRAPPER and Mandriva. I was able to do a scan and see the networks but for some reason it wont scan so I can make sure I have all the settings correct. Is there a problem with the Airlink AWLH3025 wifi card? Its got a TI chipset. Should I run NDISWRAPPER to see if that works with it? I wouldnt see why I should have to if the device manager in Ubuntu sees it and shows that its functioning.

Any help would be greatly appreciated. Thanks!
Bill

---

### Post by nanotube on 2006-02-21
to scan from commandline, use
```
iwlist eth0 scan
```
where you replace eth0 with your proper interface name.

sorry, dont know any specifics on your wifi card, so that's all i can offer.

---

### Post by txwylde on 2006-02-22
That does not work. It tells me scanning is not permitable. I have used the scan command before in Mandiva and it worked fine. 

I am going to swap cards with a DLINK one and see if that works.

---

