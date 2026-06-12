---
title: "wakeonlan only works if sleeper is Windows OS"
date: 2012-05-15
forum: General Help
---

### Post by Rebelli0us on 2012-05-15
I can wake up a machine on my network like this:

```
wakeonlan 70:71:BC:48:F3:F2
```

but only if it is running Windows. When it's running Ubuntu the command has no effect. Any ideas?

---

### Post by Cheesemill on 2012-05-15
The OS shouldn't make a difference at all as WOL is handled by the BIOS.

Are you trying to wake the same machine running Windows and then Ubuntu or are these 2 different machines?
If it's different machines then make sure that WOL is actually supported by the motherboard and switched on in the BIOS on the Ubuntu machine.

---

### Post by Rebelli0us on 2012-05-15
> **Cheesemill said:**
> The OS shouldn't make a difference at all as WOL is handled by the BIOS.

Are you trying to wake the same machine running Windows and then Ubuntu or are these 2 different machines?
If it's different machines then make sure that WOL is actually supported by the motherboard and switched on in the BIOS on the Ubuntu machine.


Thank you. It's the same machine, when suspended S3 while running Windows, wakeonlan works fine. But when running Ubuntu it will not resume.

When target is running Windows, I can even wake it from a Windows VM guest with WolCmd.exe

---

### Post by Rebelli0us on 2012-05-16
In windows, you often have to enable “magic packet” for the adapter in Device Manager. There’s probably something similar in Linux, but there is no Device Manager in Linux?

---

### Post by bruno9779 on 2012-05-16
Try:

```
sudo apt-get install ethtool
```

Run the following command to enable it:
```
sudo ethtool -s eth0 wol g
```

This can be verified running ethtool on ethX (where X is the name/number of the Ethernet device).
```
sudo ethtool eth0
```

You should see something like this ("g" indicates Wake on MagicPacket is enabled):
```
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	.....
        .....
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes
```

From [here]("http://wiki.xbmc.org/index.php?title=HOW-TO:Set_up_Wake-On-Lan_(Ubuntu)")

---

### Post by Rebelli0us on 2012-05-16
I think I've found it:

```
sudo ethtool -s eth0 wol g
```

wakeonlan works now, I hope the setting is permanent!

---

### Post by Rebelli0us on 2012-05-16
> **bruno9779 said:**
> Try:

```
sudo apt-get install ethtool
```

Run the following command to enable it:
```
sudo ethtool -s eth0 wol g
```

This can be verified running ethtool on ethX (where X is the name/number of the Ethernet device).
```
sudo ethtool eth0
```

You should see something like this ("g" indicates Wake on MagicPacket is enabled):
```
Settings for eth0:
	Supported ports: [ MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	.....
        .....
	Auto-negotiation: on
	Supports Wake-on: g
	Wake-on: g
	Link detected: yes
```

From [here]("http://wiki.xbmc.org/index.php?title=HOW-TO:Set_up_Wake-On-Lan_(Ubuntu)")

Thank you, I just found the link but it looks much too technical. It seems to imply that the command to enable WOL is NOT permanent, and their solution(s) might as well be in Chinese.:popcorn:

---

### Post by bruno9779 on 2012-05-16
there are easier ways to go about that.

You could make a very simple bash script, put it in your path and add it to the startup applications.

let me know if you need any help with that. (in a couple of hours I will have the time to make the script for you)

---

### Post by Rebelli0us on 2012-05-16
> **bruno9779 said:**
> there are easier ways to go about that.

You could make a very simple bash script, put it in your path and add it to the startup applications.

let me know if you need any help with that. (in a couple of hours I will have the time to make the script for you)

Thank you. I’m googling and it seems that the way to enable WOL **permanently** varies by distro AND version, e.g. adding the command in /etc/rc.local in versions after Ubuntu 10.04 does not work!

This is the best I found:
[http://wiki.debian.org/WakeOnLan](http://wiki.debian.org/WakeOnLan)

in /etc/network/interfaces add this at the end

```
iface eth0 inet dhcp
        ethernet-wol g
```

What do you think?

---

### Post by bruno9779 on 2012-05-16
I have found this:

[https://bugs.launchpad.net/ubuntu/+source/maas-provision/+bug/992522](https://bugs.launchpad.net/ubuntu/+source/maas-provision/+bug/992522)

I think you have to run ethtool manually everytime you reboot for now. If you suspend most of the times you should be fine

---

