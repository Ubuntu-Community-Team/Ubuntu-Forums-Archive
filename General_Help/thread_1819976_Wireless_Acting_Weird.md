---
title: "Wireless Acting Weird"
date: 2011-08-07
forum: General Help
---

### Post by Infamous Blob on 2011-08-07
Hello, first post at all so hii :)
Just installed Ubuntu on my machine alongside WIndows 7 Professional, it's a desktop computer with wireless networking, not sure what card it has tho.
Any-hows, since installing the wireless has acting very oddly under Ubuntu, the icon sometimes spends forever pulsing (as if it were loading up the connection) and, after about five minutes, it asks me for the password, and then nags me again a bit later, the whole time it being disconnected. It doesn't ever connect when it gets like this, and it needs a reboot to make it work again. It seems totally random as to whether it does this or not.
This isn't too much of a problem, rebooting takes about 20 seconds, but I'd like to get it working properly. The wireless does sometimes misbehaves under Windows, but the only issue is it just doesn't connect automatically and requires me to do it manually. It's not as severe as this.
Soo, all help appreciated ^^
Thanks in advance :)

---

### Post by garvinrick4 on 2011-08-07
Open a terminal in ubuntu and run this and post results:
```
sudo lshw -C network
```

---

### Post by Infamous Blob on 2011-08-07
I get:

 *-network               
       description: Ethernet interface
       product: AR8131 Gigabit Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: c0
       serial: 40:61:86:58:da:d5
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=atl1c driverversion=1.0.1.0-NAPI firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:feac0000-feafffff ioport:d800(size=128)
  *-network
       description: Wireless interface
       product: RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 7
       bus info: pci@0000:03:07.0
       logical name: wlan0
       version: 20
       serial: 00:27:19:e5:3d:2f
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8180 driverversion=2.6.38-10-generic firmware=N/A ip=192.168.1.65 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg
       resources: irq:22 ioport:e800(size=256) memory:febffc00-febffdff

---

### Post by Matt__ on 2011-08-07
my rtl8192 exhibited similar problems due to two drivers trying to work at the same time.

do```
sudo lshw | grep RTL8185
```and see if you have more than one driver module loaded, if so blacklist one of them in```
/etc/modprobe.d/blacklist.conf
```

if this dosnt work then try blacklisting the other :)

---

### Post by Infamous Blob on 2011-08-08
Hmmm, thanks, but that outputs nothing in the terminal, it just comes up with PCI (sysf) and then something else (possibly SCSF, but it only flashes across the the screen for a second)... not sure what that means :-/

---

### Post by Matt__ on 2011-08-08
[COLOR="DimGray"]#odd..so what driver is it using?[/COLOR]

try the command again changing rtl8185 to rtl8180 (I was looking at card designation and not the listed driver :P )


Also realtek supply a linux driver for that card [_>>here<<_](http://www.realtek.com/downloads/downloadsview.aspx?langid=1&pnid=1&pfid=1&level=6&conn=5&downtypeid=3&getdown=false&downloads=true)

---

### Post by Infamous Blob on 2011-08-08
Changing it outputted:
                configuration: broadcast=yes driver=rtl8180 driverversion=2.6.38-10-generic firmware=N/A ip=192.168.1.65 latency=64 link=yes maxlatency=64 mingnt=32 multicast=yes wireless=IEEE 802.11bg

I'll install that driver tho and see what happens :)
Thanks

edit: I actually can't work out how to install the driver, one of the big things I miss from Windows are .exe files. I can't find an installer script in there either and I don't quite get what the read-mes are asking me to do...

---

### Post by Matt__ on 2011-08-08
I downloaded that driver..its OLD! for 8.04 but if you still want to try it
open a terminal (assuming you have files on desktop) commands one by one
```

cd Desktop/rtl8185_linux_26.1031.1207.2009.release/

sudo su

./configure

make

make install

```after this you may want to blacklist rtl8180 (unless this is the same driver!!) in the location listed above, just add the line to the end of the text file ```
blacklist rtl8180
```The equivalent to a .exe is a .deb which opens the software centre or uses Gdebi to auto install...there wasnt one available that I could find.

---

