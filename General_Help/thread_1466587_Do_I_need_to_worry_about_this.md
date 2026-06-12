---
title: "Do I need to worry about this?"
date: 2010-04-30
forum: General Help
---

### Post by itsols on 2010-04-30
I just happened to look at my System Log and I found these lines repeatedly showing up:

> date & time: MyComputer dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 8
date & time: MyComputer dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 9
date & time: MyComputer dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
date & time: MyComputer dhclient: DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 2
date & time: MyComputer dhclient: No DHCPOFFERS received.
date & time: MyComputer dhclient: No working leases in persistent database - sleeping.

I don't know what it means and I'd like to know if this is something to be concerned about.

Many thanks!

---

### Post by dino99 on 2010-04-30
at first glance its the normal discovering process, trying to activate the network
have issue to connect on web ?

into terminal, run: ifconfig
if it dont return errors, dont worry

---

### Post by itsols on 2010-04-30
Thank you for the quick response.

I'm on a laptop. It's got Wifi. But I'm wired right now. And I'm not having any problem with the network. I'm online as I write this message.

But I DO have issues with Wi-Fi in Ubuntu (it's dual boot and on Windows it's fine). I'm not interested in the Wi-Fi for now but do you think these lines are connected to it?

Thanks again.

---

