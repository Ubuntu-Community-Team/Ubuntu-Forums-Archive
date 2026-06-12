---
title: "Network initialization hangs up boot"
date: 2006-04-02
forum: General Help
---

### Post by ninjaPants on 2006-04-02
Seems lately my laptop hangs for a long time at the "Initializing network interfaces" stage of boot. I found [this thread]("http://ubuntuforums.org/showthread.php?t=16319") from the archives, but I have more questions. 

Running dmesg shows a lot of entries like this: 
```
[4354430.728000] eth0: New link status: Association Failed (0006)
[4354431.078000] eth0: New link status: Disconnected (0002)
[4354431.426000] eth0: New link status: Connected (0001)
[4354433.107000] eth0: New link status: Disconnected (0002)
[4354434.696000] eth0: New link status: Connected (0001)
[4354453.070000] eth1: no IPv6 routers present
```

Based on this, I figure my wifi card at eth0 is failing because it wants to connect to my secure network. Also, I mostly use the LAN connection (eth1, which is set as default) to my router anyways. So I poked around /etc/network/interfaces as suggested above. The only reference to the wifi card is
```
iface eth0 inet dhcp
```
So if I comment this out, it won't initialize on boot, right? 

I'm worried, however that I'll piss off network manager by doing this. I just installed it, so I'm not sure it'll even start up. In a perfect world I could use the wifi button on my hp pavillion ze5375us to do it, but I looked into it, and unless I find a specific howto under a rock somewhere, I won't bother. 

The better option seems to be to make a launcher and add it to the panel that runs this command:
```
sudo ifup eth0 && gksudo NetworkManager
```

I'm kinda shaky on syntax though... is that right?

Attached are the full output of dmesg and my /etc/network/interfaces files.

Thanks in advance!!
Andrew

---

