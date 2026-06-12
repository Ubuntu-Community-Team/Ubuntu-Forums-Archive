---
title: "What is going on...???"
date: 2011-05-18
forum: General Help
---

### Post by robertcoulson on 2011-05-18
I installed firestarter to try it out and this IP address is appearing continuously without stopping...Does this mean he is on my machine...Or trying to get on my machine (see attachment)
Thanks....Robert

---

### Post by Jonauterrr on 2011-05-18
Is your router locked or unlocked? If there is no WEP password set then anyone can connect to your router.

---

### Post by robertcoulson on 2011-05-18
Oh...It's locked tighter than a frog's A** underwater, and that is water tight...(ha,ha)....It does have a good password....
Robert

---

### Post by robertcoulson on 2011-05-18
By the way...I tracked his IP address to China...???
Robert

---

### Post by robertcoulson on 2011-05-18
This scares me...Look at the "destination"....Yikes
Robert

Time:May 18 18:45:21 Direction: Unknown In:wlan0 Out: Port:53959 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:May 18 18:45:22 Direction: Unknown In:wlan0 Out: Port:60572 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:May 18 18:45:24 Direction: Unknown In:wlan0 Out: Port:53959 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:May 18 18:45:25 Direction: Unknown In:wlan0 Out: Port:60572 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:May 18 18:45:30 Direction: Unknown In:wlan0 Out: Port:53959 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:May 18 18:45:31 Direction: Unknown In:wlan0 Out: Port:60572 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:May 18 18:46:52 Direction: Unknown In:wlan0 Out: Port:53959 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:May 18 18:47:01 Direction: Unknown In:wlan0 Out: Port:60572 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:May 18 18:49:06 Direction: Unknown In:wlan0 Out: Port:53959 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown
Time:May 18 18:50:02 Direction: Unknown In:wlan0 Out: Port:60572 Source:219.76.173.47 Destination:192.168.1.4 Length:48 TOS:0x00 Protocol:TCP Service:Unknown

---

### Post by wildmanne39 on 2011-05-18
> **robertcoulson said:**
> I installed firestarter to try it out and this IP address is appearing continuously without stopping...Does this mean he is on my machine...Or trying to get on my machine (see attachment)
Thanks....Robert

Hi, does it show that it is blocked,if so dont worry about it, if not block the port being used. I have never had a problem with anyone breaking through fire starter firewall.

---

### Post by robertcoulson on 2011-05-18
I think this attachment shows me that it IS blocked...???
Hope I am reading it correctly...???
Robert

---

### Post by wildmanne39 on 2011-05-18
> **robertcoulson said:**
> I think this attachment shows me that it IS blocked...???
Hope I am reading it correctly...???
Robert

Hi, it does not show any outside connetions your good.):P

---

### Post by robertcoulson on 2011-05-18
Thank you wildmanne39....Was a little worried...Do I really need irestarter then...???
Robert

---

### Post by wildmanne39 on 2011-05-18
> **robertcoulson said:**
> Thank you wildmanne39....Was a little worried...Do I really need irestarter then...???
Robert

Hi, it is a good idea, just to be on the safe side.if your problem or question is resolved, would you please go to the top of the page and mark this thread solved be clicking on forum tools. Thank you so much.
:D

---

### Post by Thewhistlingwind on 2011-05-18
> **robertcoulson said:**
> Thank you wildmanne39....Was a little worried...Do I really need irestarter then...???


A firewall is generally considered good practice. If there's no services running, yes, you can get away with not using a firewall. The difference is, do you really want to leave yourself exposed like that in the case of a mistake using apt-get? My only criticism of firestarter is that I keep reading that it's a dead project. If this is the case, using unmaintained software, especially unmaintained SECURITY software, is dangerous.

EDIT: The wikipedia article is not encouraging

---

### Post by robertcoulson on 2011-05-18
No...Thank you...Closed as requested.
Robert

---

### Post by robertcoulson on 2011-05-18
Thewhistlingwind...If Firestarter is not the best fire wall...Which one do you suggest I use...???
Robert

---

### Post by Thewhistlingwind on 2011-05-18
> **robertcoulson said:**
> Thewhistlingwind...If Firestarter is not the best fire wall...Which one do you suggest I use...???
Robert

I don't have a recommendation (Besides not using a product that's last stable release was 2005 [http://en.wikipedia.org/wiki/Firestarter_%28firewall%29](http://en.wikipedia.org/wiki/Firestarter_%28firewall%29)), but this IS a sticky.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by Larkspur on 2011-05-18
I'd go for gufw.  It's simple, it's still supported, and it doesn't let you know what connections it has denied every two seconds like Firestarter (though it does keep a record in the logs).

---

### Post by robertcoulson on 2011-05-18
Thanks Larkspur...I am giving GUFW a try right now...
Robert

---

