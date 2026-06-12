---
title: "Random Wireless Disconnects"
date: 2011-05-13
forum: General Help
---

### Post by Quarkrad on 2011-05-13
_Newbie running 64bit 10.10_   I'm having drop out problems (again) with my wireless connection - logging in/out doesn't make any difference or sudo commands to kill networking and restart - the only way to get connection again is to restart.  Googling has lots of options but there are so many, it all gets a bit confusing.  I use wireless (rt73usb driver that appears to be problematic in 10.10 and 11.04) with a static ip address (192.168.1.4), my Connection Information/Active Network Connections says  802.11 WiFi (wlan0).  My current /etc/network/interfaces file looks like:

auto eth0
iface eth0 inet static
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1

(should the first line not read auto wlan0?).

If edit the etc/network/interfaces file to this will it improve things?

auto wlan0
iface wlan0 inet static
wireless-essid XXXXXXXXXXXX(Broadcast name of my router)
wireless-key XXXXXXXXXXX (I use wap2 so this would be my wap2 security key)
address 192.168.1.4
netmask 255.255.255.0
gateway 192.168.1.1

---

### Post by Quarkrad on 2011-05-13
So far so good.  These settings work and no drop outs/disconnects so far.

---

### Post by Quarkrad on 2011-05-14
Spoke too soon - back to disconnects.  Something somewhere appears to decide to disconnect from the router and that's it.  The only way to establish connection is to reboot the pc.  Does seem odd that it works for a while (so is everything OK?) and then Bang.  Any help appreciated - looks like I still need winXP to communicate to the outside world.  Depressing that (internet/router connection wise) winXP works 100% but not Ubuntu.  As I cannot ping the router when this happens could the problem be this driver issue I occasionally read about?

---

### Post by Quarkrad on 2011-05-16
bump - now I'm starting to get no connection when I switch on.

---

### Post by nothingspecial on 2011-05-16
I  see that you did nevermind

---

### Post by Quarkrad on 2011-05-16
Errr - newbie here.  Is this supposed to mean something?

---

### Post by nothingspecial on 2011-05-16
> **Quarkrad said:**
> Errr - newbie here.  Is this supposed to mean something?

I'm sorry Quarkrad :D

I posted asking you to give details of your wireless card.........

...... after posting, I realised that you already had, so I edited my post.

I am not familiar with the module or the wireless card.

Sorry to waste your time. No offence meant :D

---

### Post by Quarkrad on 2011-05-27
Bump - help

Have been on OK but now it's now letting me on even after re-booting.  The netwrok icon shows it's connected at full strength but I cannot ping my router or get internet connection.

---

### Post by LordNeo on 2011-05-27
First of all, i would like to suggest you to install WICD, i've found some wireless card that just work with WICD and not with the default network manager.
Also, please try disconnecting from your wireless network, wipe the configuration manually introduced in the interfaces and also clearing the configuration saved automatically in the network manager.
Does your router use "automatic" channel selection or "protected mode"?

---

### Post by Quarkrad on 2011-05-28
Thank you - I'm a newbie so not sure how to: 

*wipe the configuration manually introduced in the interfaces and also clearing the configuration saved automatically in the network manager.*

I'm afraid I'm also not sure about the channel protection/automation.  I have a Huawei Echolife 520S - I can select anyone of 13 channels or put it in automatic mode - currently I have it set to channel 10.  Not sure about the 'protected' mode though.

Sorry - but appreciate your help.

---

### Post by Quarkrad on 2011-05-30
bump

---

### Post by Quarkrad on 2011-06-03
This is not the cause of my random dis-connects but I have noted, on more than one occasion, that my connection can be 'dumped' (I cannot reconnect unless I reboot) when another wireless laptop boots up in the house.  Both PC's are configured with static IP addresses - one is 192.168.1.4 and the other is 192.168.1.7 - strange, to me, why this keeps happening, how does the other machine boot me off my connection?  Once I have rebooted both machines are happy with their connections (both run Ubuntu 10.10).

---

