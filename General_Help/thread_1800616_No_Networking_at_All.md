---
title: "No Networking at All"
date: 2011-07-09
forum: General Help
---

### Post by aldee96 on 2011-07-09
I'm using ubuntu 11.04 an i was trying to follow the instructions in here : _[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)_ and here : [U][https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless](https://help.ubuntu.com/community/WifiDocs/ShareEthernetConnectionThroughWireless)
[/U]
I've followed all of the instruction, after all i realized my internet  connection is stopped, i click the network manager applet and both my  wired and wireless connection are "Device not Managed", then  i click ***"Edit Connections" ***and i realised my **wired **connections(that used to be **Auto Eth0**)  is no longer there, i've tried to create a new connection with the same  name, no result at all. Then I restarted my laptop then the network  applet **disappeared**.

Honestly I'm panic, then i try to ping by this instructions from _[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)_ (i'm able to done this because of the webpage that cached by firefox, so i could read it again after the restart)

>  **Testing**

   Once you  have two or more computers connected to the ad hoc network, all of them  showing the same cell number and having different IP addresses, then try  pinging one from the others. 
 ping 169.254.34.2  

it resulted with some output, i've read some thread that says ***"if you could ping yourself, then it's just a little problem that hitting you". ***so now i'm a little bit less panic. But i still need some help

---

### Post by AgentZ86 on 2011-07-09
It sounds like your router and/or wireless hub or modem to the internet got fried.

At least at first glance.

I don't know why the applet would disappear though that seems strange.

but have you tried uplugging the power to your routers and wireless connections for 60 seconds or so and then plugging them back in again.

Then restart the computer and  see if you get internet at least to narrow things down a bit to be sure it's computer related.

Thats all I know, sorry I can't be more help

---

### Post by grahammechanical on 2011-07-09
Try this. It might just work.

Open a terminal and

```
cat /etc/network/interfaces
```

It should list only

> auto lo
iface lo inet loopback

in the interfaces file. Edit out anything else.

```
gk sudo gedit /etc/network/interfaces
```

Then reboot and see if the device not managed message has gone and network manager is detecting networks.

This worked for me when I had an install of Ubuntu Studio giving the devices not managed message.

regards.

---

