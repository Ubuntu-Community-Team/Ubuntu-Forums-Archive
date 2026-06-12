---
title: "Wireless Connected But Can't Browse Web"
date: 2011-08-01
forum: General Help
---

### Post by Static Fallen on 2011-08-01
Hey, thanks in advance. I am fairly new to ubuntu and I am already having a few issues. When I turn on my computer and sign in it is supposed to auto connect to my wireless internet(which it does). But once it is connected I go and open the web browser(I have tried chronium and firefox) and I loads for a while then says it cannot connect even though it shows in the top right that I am connected to my wireless internet.

I am running ubuntu 11.04 and I have tried to do a clean install, but I still receive the same problem.

I had the wireless working a few days ago on my laptop, and the wireless works fine still on my other computer.

Here are some terminal outputs if anyone needs them-

Iwconfig
```

lo                    no wireless extensions.

eth0                  no wireless extensions.

wlan0                 IEEE 802.11abgn. ESSID: "myqwest7019"
                      Mode:Managed. Frequency:2.462 GHz. Access Point:  00:26:B8:F9:17:80
                      Bit Rate=78 Mb/s.   Tx-Power=14 dBm
                      Retry    long  limit:7     RTS thr:off        Fragment thr:off
                      Power Management:off
                      Link Quality=56/70    Signal level=-54 dBm
                      Rx invalid nwid:0   Rx invalid crypt:0    Rx invalid frag:0
                      Tx excessive retries:0   Invalid misc:37    Missed beacon:0

```

route -n
```

Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.0.0     0.0.0.0         255.255.255.0   U     2      0        0 wlan0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 wlan0
0.0.0.0         192.168.0.1     0.0.0.0         UG    0      0        0 wlan0

```

I also cannot ping website from terminal if that counts for anything...

---

### Post by Foxheadz on 2011-08-01
Hmm so it appears you're connected to your router and the internet, do you know what wireless card you have? you can find out bu running ```
 lspci | grep -i network
```?

---

### Post by Static Fallen on 2011-08-01
> **Foxheadz said:**
> Hmm so it appears you're connected to your router and the internet, do you know what wireless card you have? you can find out bu running ```
 lspci | grep -i network
```?

This is what it gave me-

```

00:19.0 Ethernet controller: Intel Corporation 82566MM Gigabit Network Connection (rev 03)
10:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)

```**EDIT:** I would also like to state that I just tried to connect directly to my router with an ethernet cable and the internet works fine that way, I just cant seem to get the wireless to work :(

---

### Post by Static Fallen on 2011-08-01
Also I read on another forum that the /etc/network/interfaces file is supposed to have stuff in it but all mine has is this-

```
auto lo
iface lo inet loopback

```

---

### Post by Foxheadz on 2011-08-01
I would check out this site [http://linuxwireless.org/en/users/Drivers/iwl4965](http://linuxwireless.org/en/users/Drivers/iwl4965)
and FINAL EDIT: ok it seems new drivers arn't needed, so intead try just running ```
sudo modprobe iwl4965
``` 

oh and don't worry about /etc/network/interfaces i also have just that

---

### Post by Static Fallen on 2011-08-02
Okay I tried that but all it did was ask me for the password then nothing else happened. I still can't connect to my wifi :(

---

### Post by 3rdalbum on 2011-08-02
When your computer tries to connect to the router, the router sends information such as the IP address, default gateway, etc to the computer through a system called DHCP.

For some reason, DHCP doesn't always work properly with different combinations of operating system, router and client device.

Click on the Network Manager indicator and go to Edit Connections. Click on the Wireless tab and then click on your connection and click Edit. In the IPv4 Settings tab, change the method to Manual.

Input your IP address, subnet mask, gateway and DNS servers manually. You can just copy the settings from your other computer that works, except **make sure the last number in the IP address is different**. Click Save, close the windows, disconnect from your wifi and then connect again.

With luck, it should work now.

---

