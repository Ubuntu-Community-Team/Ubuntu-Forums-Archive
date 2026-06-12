---
title: "Cant connect to internet"
date: 2010-03-14
forum: General Help
---

### Post by yangas on 2010-03-14
Well I recently installed ubuntu on my new computer since windows wasn't working on it.  I now face the problem that I am unable to connect to the internet even though the computer is directly connected to my modem.  

02:00.0 Ethernet controller: Realtek Semiconductor Co ., Ltd.  RTL8111/8168B PCI Express Gigabit Ethernet Controller (rev 03)

That's my modem, on another forum I post on I got mixed answers one person said that it might be a driver issue.  I don't really know how to uninstall drivers and install new ones so if that's the case I would appreciate a quick help on that.  The other person said that he had the same driver and all that was missing was that I needed to do was configure my DHCP.  He then provided what I should put in terminal.  

sudo killall NetworkManager
sudo dhclient eth0

Okay so I put that command in and it tried to connect, but then just as  always it disconnected on its own.  At the end of the things that start  coming up like "DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval  " and then came a number it dd that about 8 times with intervals being  different numbers and then said "No DHCPOFFERS received." and lastly it  says "No working leases in persistent database - sleeping." and then it  ends whatever it was doing.

---

### Post by yangas on 2010-03-14
Ohh and by the way the problem is when I try to start internet connection it starts loading but then says wired connection disconnected.

---

### Post by Iowan on 2010-03-14
I doubt [this]("http://ubuntuforums.org/showthread.php?t=1156441") will help - but you can try it...

---

