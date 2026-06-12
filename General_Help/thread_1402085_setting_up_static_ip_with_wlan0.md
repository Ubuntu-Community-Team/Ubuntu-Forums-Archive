---
title: "setting up static ip with wlan0"
date: 2010-02-08
forum: General Help
---

### Post by ubudog on 2010-02-08
Hello, I am pretty new to this.  I edited the file /etc/network/interfaces and changed it from

auto lo
iface lo inet loopback

to 

auto wlan0
iface wlan0 inet static
address 192.168.1.130
netmask 255.255.255.0
gateway 192.168.1.1

I configured my router accordingly and I rebooted.  When I restart, I can't connect to any networks.  Network manager says "Device not managed".  I looked at the output of ifconfig and it said that the interface wlan0 had the ip address of 192.168.1.130.  I could not browse the internet.  I had to change back to the original to be able to post this.  Any help is appreciated. Thanks. ;)

---

### Post by Iowan on 2010-02-08
I hope you left the two "lo" lines in there...
Network Manager won't (or shouldn't) touch interfaces defined in */etc/network/interfaces*. Could you ping the gateway at 192.168.1.1?

---

### Post by ubudog on 2010-02-08
> **Iowan said:**
> I hope you left the two "lo" lines in there...
Network Manager won't (or shouldn't) touch interfaces defined in */etc/network/interfaces*. Could you ping the gateway at 192.168.1.1?

No, I didn't leave the "lo" lines in there.  I will try that.  Will post back later.

---

### Post by ubudog on 2010-02-08
OK, now I have /etc/network/interfaces as 

auto lo
iface lo inet loopback
address 192.168.1.130
netmask 255.255.255.0
gateway 192.168.1.1

Now, when I reboot, I can connect to my wireless network, but I don't get the static ip of 192.168.1.130 that I want.  By the way, I followed the directions here: [http://ubuntuforums.org/showthread.php?t=632841]("http://ubuntuforums.org/showthread.php?t=632841")  changing the part about the static ip to wlan0, because I am using wireless.

---

### Post by ubudog on 2010-02-08
Oh well, I need to find a better computer for being a server.  My Ubuntu install is pretty messed up, so I will reinstall.  Thanks for your help.

---

### Post by ubudog on 2010-02-08
Actually, I think I have it all sorted out.  Will use eth0 for static ip though.

---

### Post by Iowan on 2010-02-08
I can't guarantee the static IP will work for wlan0, but the */etc/network/interfaces* file would look like:```
auto lo
iface lo inet loopback

auto wlan0
iface wlan0 inet static
address 192.168.1.130
netmask 255.255.255.0
gateway 192.168.1.1

```

*Ordinarily*, eth0 is a wired connection - my laptop uses eth1 for wireless.

---

### Post by ubudog on 2010-02-09
Oh well, I got it working using NetworkManager.

---

