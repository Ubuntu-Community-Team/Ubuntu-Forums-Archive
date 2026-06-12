---
title: "Wicd won't stay disconnected from wireless"
date: 2012-09-22
forum: General Help
---

### Post by chellrose on 2012-09-22
I recently installed Ubuntu 11.10 on my Toshiba Satellite.  (I'm using the Trinity Desktop environment on top of that -- not sure if this makes a difference.)

Tried to find the default wireless connection program/network manager/whatever by typing
```
apropos network
```
and hunting for "network" and the like in Adept.  Nothing seemed to be installed, yet my computer was connected to the wireless (I'd connected it prior to installation from the live CD so that it could find updates during install).  Apparently it saved my settings somehow from the live CD.

Anyhow, I wanted to be able to disconnect from wireless when I'm not using it, and I couldn't find a network manager installed.  Also ```
sudo ifdown wlan0
``` didn't work.  So I installed Wicd.

I have the "Connect automatically" check-box UNCHECKED, but when I click "Disconnect" within Wicd, it will disconnect from the network for about 3 seconds, and then it connects again.

How do I make it stay disconnected until I explicitly ask it to connect?  Note that my laptop doesn't have an external wireless switch, so it's not as simple as just switching that off.

Thanks!

---

### Post by claracc on 2012-09-23
The only way I can think of doing as yo want is, in wicd manager:

untick automatically connect to this net
tick never connecting to his net

When you want to connect:

tick automatically connect to this net
untick never connecting to his net

Perhaps you have installed two network managers:

wicd
network-manager

You can see it looking for them running ps-ef in a xterm.
In the case you have two net managers installed you have to disable one of them.

---

### Post by chellrose on 2012-09-24
Thanks.

In ps -ef, I see this line which I suspect may be the culprit:
```

root      3048   862  0 18:42 ?        00:00:00 /sbin/dhclient -d -4 -sf /usr/lib/NetworkManager/nm-dhcp-client.action -pf /var/run/dhclient-wlan0.pid -lf /var/lib/dhcp/dhclient-e9fc43b3-47f

```

However, it's not clear to me how to disable it.  How would I go about doing that?  (I could kill the process, but I suspect it would just start again on next boot.)

---

### Post by claracc on 2012-09-25
About how to disable network-manager I have found this link: [https://help.ubuntu.com/community/NetworkManager](https://help.ubuntu.com/community/NetworkManager), where it is said:

> Disabling NetworkManager

According to this bug here's how to disable Network Manager without uninstalling it:

Stop network manager, in a xterm you run:

sudo stop network-manager

Create an override file for the upstart job, in a xterm, you run:

echo "manual" | sudo tee /etc/init/network-manager.override

---

### Post by chellrose on 2012-09-25
Thank you!  It seems to be functioning normally now.

---

### Post by claracc on 2012-09-26
You are welcome.

Glad you got fixed your problem.

---

