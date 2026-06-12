---
title: "Delayed boot processes?"
date: 2012-05-22
forum: General Help
---

### Post by habana on 2012-05-22
A few days ago I posted the following in the Networks and Wireless forum:

> **Delayed connection to network**

I have installed 12.04 on a SSD and my computer boots up in ten seconds or so from switchon. No complaints there! I have Thunderbird in my Startup Preferences but this initially reports "no connection to server" as the network doesn't connect for several more seconds. I have a hard wired 100 Mb/s connection to my router which is on 24/7. Once the network connects, I hit the "Get mail" button and my emails download.

Is this delay caused by my router or by some delayed Network Manager handshaking process? I use DHCP so presumably the router polls the four ports in sequence. Would it be faster if I changed to a fixed IP address?

Obviously this isn't a show stopper but it would be nice to speed it up a little and learn a bit more about how it all works! Any advice on how to proceed would be appreciated.

Ubuntu 12.04 64bit
Draytek Vigor2700VG

I have since discovered that it is not only my network connection that does not work straight away; the Unity Dash window will open immediately but is blank for the same period noted above, which I now measure as 7 seconds. Applications I can start from the Launcher open immediately. I have installed Bootchart which reports a boot time of 5 seconds. The chart runs for another 2 seconds or so but no processes seem to be running during this time. Are there some relevant processes that Bootchart doesn't record?

It is my experience with previous versions of Ubuntu that, unlike Windows, everything works as soon as the desktop is displayed. Has this changed or is my (minor) problem something to do with the much faster processing speed of the SSD?

All help appreciated.

---

### Post by habana on 2012-05-23
Bump

---

### Post by d4m1r on 2012-05-23
No, nothing can really be done. On a related note, how are your partitions setup?

Seems like Ubuntu is loading certain elements faster than others and while I know SSD usually work flawless under Ubuntu, I can imagine they might not be optimal in ALL scenario's. As for your Thunderbird issue, it is definitely not an issue with your network/router but with network-manager most likely. By the time you login and Thunderbird goes to check for new messages, network-manager does not initialize in time.

Simply fix would to remove it from startup applications, wait >10 seconds after logging in, and launch it manually like I do ;)

---

### Post by habana on 2012-05-24
> Simply fix would to remove it from startup applications, wait >10 seconds after logging in, and launch it manually like I do 

Thanks, I've already done that! I take it your system behaves in the same manner?

---

