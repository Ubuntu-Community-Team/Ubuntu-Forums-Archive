---
title: "can't enable wireless"
date: 2006-04-19
forum: General Help
---

### Post by bakunin on 2006-04-19
Hi,
starting the network settings in the system settings shows me two interfaces, eth0 and eth1. I've disabled eth0 with sudo ifconfig eth0 down, but I can't enable eth1 (my wireless one). If I click on 'enable interface' it turns green for a second and then flips back to red = disabled.
What can I do to enable it?
I have a Dell Inspiron 630 m

---

### Post by uteck on 2006-04-19
Does it have the Intel wifi, ipw2100 or ipw2200?  If so you may need to install the firmware for the chip.  [http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net)

---

### Post by bakunin on 2006-04-20
lspci gives me
Intel Corporation PRO/Wireless 2915ABG MiniPCI Adapter

is this the information you asked for?

---

### Post by mexlinux on 2006-04-20
[QUOTE=bakunin]
I have a Dell Inspiron 630 m[/QUOTE]
me too.

I must tell, Wireless is very crappy in kubuntu.
The way I got it to work is doing it by hand.
Set up properly the files:
/etc/network/interfaces
/etc/resolv.conf

If you are moving, instal wifi-radar.

---

### Post by mexlinux on 2006-04-20
[QUOTE=uteck]Does it have the Intel wifi, ipw2100 or ipw2200?  If so you may need to install the firmware for the chip.  [http://ipw2200.sourceforge.net](http://ipw2200.sourceforge.net)[/QUOTE]

I never installed this thing.... but it's working! does it provide eny extra functionallity, speed improvement, etc?

---

### Post by bakunin on 2006-04-20
[QUOTE=mexlinux]me too.

I must tell, Wireless is very crappy in kubuntu.
The way I got it to work is doing it by hand.
Set up properly the files:
/etc/network/interfaces
/etc/resolv.conf

If you are moving, instal wifi-radar.[/QUOTE]

What exactly has to be in these files? I'm a newbie...

---

### Post by mexlinux on 2006-04-20
[QUOTE=bakunin]What exactly has to be in these files? I'm a newbie...[/QUOTE]

Well, that depends on how are you going to connect...
but in /etc/network/interfeces you have to put the general configuration of the card, 
you can read the manual pages:
FROM CONSOLE man interfaces
FROM KONQUEROR man:interfaces

If your are connecting with dinamyc IP with open wep, this will be a typical configuration:

```

auto lo
iface lo inet loopback

iface eth1 inet dhcp       
        wireless-mode managed
        wireless-essid xxxxx
        wireless-key xxxx

```

in /etc/resolv.conf
You must specify your name sarver.
```

nameserver xxx.xxx.xxx.xxx

```

You will find this page very usefull:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")

---

### Post by bakunin on 2006-04-20
If your are connecting with dinamyc IP with open wep, this will be a typical configuration:

```

auto lo
iface lo inet loopback

iface eth1 inet dhcp       
        wireless-mode managed
        wireless-essid xxxxx
        wireless-key xxxx

```

in /etc/resolv.conf
You must specify your name sarver.
```

nameserver xxx.xxx.xxx.xxx

```

You will find this page very usefull:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")[/QUOTE]



I've changed the first things, and now I can open the "configure interface" page in the network settings, where I find the data I typed in. However, when trying to enable it it still flips back to disabled after a second or so. 
What is a nameserver? Where can I find it?
And ifconfig doesn't list an IP address...
It's very frustrating...

---

### Post by mexlinux on 2006-04-20
In order tobe of any help, I will need mor info:
Please, post the contents of your files.
Say, to what are you trying to connect?..I guess you are comming from windows, how did you conected there?

Have you read this:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide]("https://wiki.ubuntu.com/WirelessTroubleshootingGuide")

Have you installed wifi-radar? --Maybe this is all you need(?)

---

### Post by bakunin on 2006-04-21
You're help is very much appreciated :)
I've installed wifi-radar, it tries to connect to eth2, which fails, even though I've changed the wifi-radar.conf to "interface = eth1".

I'm not moving from windows, I've used kubuntu for work and installed it on my private laptop now. I haven't got internet access at all at the moment; I'm using a friends mac and blootooth for file transfer :(

Here some outputs:

iwconfig eth1
eth1      unassociated  ESSID:off/any
          Mode:Managed  Channel=0  Access Point: Not-Associated
          Bit Rate=0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sudo ifconfig eth1
Password:
eth1      Link encap:Ethernet  HWaddr 00:16:6F:4D:42:3B
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:849 errors:0 dropped:0 overruns:0 frame:0
          TX packets:314 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:177 Base address:0x6000 Memory:dfbfd000-dfbfdfff

sudo iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:11:24:0A:C0:19
                    ESSID:"Marco Polo Power"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:13
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=75/100  Signal level=-54 dBm
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra: Last beacon: 2313ms ago
          Cell 02 - Address: 00:11:24:0E:A1:9F
                    ESSID:"Marco Polo Power"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:13
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=70/100  Signal level=-58 dBm
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra: Last beacon: 6020ms ago

sudo lshw -C network
  *-usb
       description: Bluetooth wireless interface
       product: Wireless 350 Bluetooth
       vendor: Dell Computer Corp.
       physical id: 1
       bus info: usb@2:1
       version: 16.57
       capabilities: bluetooth usb-2.00
       configuration: driver=hci_usb maxpower=0mA speed=12.0MB/s
  *-network:0
       description: Ethernet interface
       product: BCM4401-B0 100Base-TX
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 02
       serial: 00:14:22:99:c2:37
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=b44 driverversion=0.97 duplex=half ip=150.203.179.127 link=no multicast=yes port=twisted pair speed=10MB/s
       resources: iomemory:dfbfe000-dfbfffff irq:209
  *-network:1
       description: Wireless interface
       product: PRO/Wireless 2915ABG MiniPCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@02:03.0
       logical name: eth1
       version: 05
       serial: 00:16:6f:4d:42:3b
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2200 driverversion=1.1.1 firmware=ABG:9.0.2.6 (Mar 22 2005) link=no multicast=yes wireless=unassociated
       resources: iomemory:dfbfd000-dfbfdfff irq:177

content of /etc/network/interfaces

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
iface eth0 inet static
        address 150.203.179.127
        netmask 255.255.248.0
        network 150.203.176.0
        broadcast 150.203.183.255
        gateway 150.203.176.1
        # dns-* options are implemented by the resolvconf package, if installed
        dns-nameservers 150.203.1.10
        dns-search anu.edu.au

iface eth1 inet dhcp
        wireless-mode managed
        wireless-essid Marco Polo Power
        wireless-key s:****************

---

### Post by mexlinux on 2006-04-21
Your problem is the "unassociated", which I'm not sure from hat what the problem is, but I wil say:

From your iwlist output, you are not having a wirlessconnetion to anything.
But your iwlist says your nic is working.
So first thing to do will be to establish your connection.
Your /etc/network/interfaces seems ok...but
-Try Master instead of Managed
-I'm not sure about the Spaces in the essid, try with quotes  "Marco Polo Power".
-Are you sure you are using an ascii key? (if not ascii, remove the s:   )

 Use the Troubleshot link I proposed in this chapter:
4.3. Router Connection

---

### Post by RedFoxEvan on 2006-04-21
Hi, Im net to Ubuntu/Kubuntu, and Im also on AOL, Once ive installed either ubuntu or Kubuntu, It cant seem to find thge network, yet when i switch back to XP, I am connected straight away :S  (Btw im on wireless)

---

### Post by bakunin on 2006-04-23
[QUOTE=mexlinux]Your problem is the "unassociated", which I'm not sure from hat what the problem is, but I wil say:

From your iwlist output, you are not having a wirlessconnetion to anything.
But your iwlist says your nic is working.
So first thing to do will be to establish your connection.
Your /etc/network/interfaces seems ok...but
-Try Master instead of Managed
-I'm not sure about the Spaces in the essid, try with quotes  "Marco Polo Power".
-Are you sure you are using an ascii key? (if not ascii, remove the s:   )

 Use the Troubleshot link I proposed in this chapter:
4.3. Router Connection[/QUOTE]

I`ve found the appropriate wifi-radar.conf and changed interface from eth2 to eth1. Now wifi-radar is working and I clearly see Marco Polo Power at full strength. However, I cannot obtain a IP, and wifi-radar tends to get stuck trying to connect. I've played around with Master/Managed, I'm sure about the essid and the key is a German word, so I assume it's not hexadecimal but ascii. I've also played with open/restricted.

I've tried the direct connection to the router via iwconfig as explained in 4.3, but I lack knowledge of ap and it didn't work.
What else can I do? How can I get access point and IP address?

What link exactly were you referring to when mentioning 4.3? Sorry, but I'm very unexperienced and have to be told everything in easy steps.

Today there's a funny thing with wifi-radar in that it doesn't want to change back from Master to Managed, even though I'm running it with sudo of course.

In any case, thanks for helping me, and I hope we're getting there in the end.

---

### Post by mexlinux on 2006-04-23
OK, we are getting closer...
wifi-radar worked the same for me at the beging, this is what I did, it might work for you.
-Do a System update (with adept updater program) there is a dhclient update.
-Dissable the wifi-radar daemon (you can do that from a module in kcontrol).
-Make the change proposed in this bug 
[https://launchpad.net/distros/ubuntu/+source/wifi-radar/+bug/4033]("https://launchpad.net/distros/ubuntu/+source/wifi-radar/+bug/4033") (backup you file, it's /usr/sbin/wifi-radar).

I hope that's the solution

---

### Post by bakunin on 2006-04-25
[QUOTE=mexlinux]OK, we are getting closer...
wifi-radar worked the same for me at the beging, this is what I did, it might work for you.
-Do a System update (with adept updater program) there is a dhclient update.
-Dissable the wifi-radar daemon (you can do that from a module in kcontrol).
-Make the change proposed in this bug 
[https://launchpad.net/distros/ubuntu/+source/wifi-radar/+bug/4033]("https://launchpad.net/distros/ubuntu/+source/wifi-radar/+bug/4033") (backup you file, it's /usr/sbin/wifi-radar).

I hope that's the solution[/QUOTE]

1) At the moment, I can't connect to the internet, only bluetooth is working. I guess, I cant update dhclient with adept. I might try to get the necessary files manually, but at my state of experience this seems daunting.
2) I couldnt find wifi-radar daemon in kcontrol. Where exactly should I look for it? The only thing I find is "Wireless Network" where I can set Config 1 to 4 and Vendor 1, but there's no daemon.
3) I did the proposed changes, but I didn't help so far...

---

### Post by mexlinux on 2006-04-25
The wifi-daemon is service.
You have to go to system services and stop it, ans dissable it at boot

---

### Post by bakunin on 2006-04-26
[QUOTE=mexlinux]The wifi-daemon is service.
You have to go to system services and stop it, ans dissable it at boot[/QUOTE]

Ok, I did everything you told me (could connect to the internet via eth0 in the meantime). However, wifi-radar is still not working. I get error messages like

wifi-radar
Error for wireless request "Set Frequency" (8B04) :
    SET failed on device eth1 ; Invalid argument.
Traceback (most recent call last):
  File "/usr/sbin/wifi-radar", line 1005, in connect_profile
    connect_to_network( ssid, connect_status_window )
  File "/usr/sbin/wifi-radar", line 385, in connect_to_network
    os.kill( int(open(DHCP_PIDFILE, mode='r').readline()), signal.SIGTERM )
ValueError: invalid literal for int():

here iwlist again:

iwlist eth1 scanning
eth1      Scan completed :
          Cell 01 - Address: 00:11:24:0E:A1:9F
                    ESSID:"Marco Polo Power"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:13
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=95/100  Signal level=-32 dBm
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra: Last beacon: 1113ms ago
          Cell 02 - Address: 00:11:24:0A:C0:19
                    ESSID:"Marco Polo Power"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:13
                    Encryption key:on
                    Bit Rates:54 Mb/s
                    Extra: Rates (Mb/s): 1 2 5.5 6 9 11 12 18 24 36 48 54
                    Quality=70/100  Signal level=-58 dBm
                    Extra:wpa_ie=dd160050f20101000050f20201000050f20201000050f202
                    Extra: Last beacon: 1112ms ago

Is there anything else I can do? Are there hardware options?

---

### Post by wh0rd on 2006-04-27
I like KDE a lot, but your telling me there isn't a single network manager with GUI to handle the basic networking needs of a user?  I don't really wanna' use Gnome! There has to be a simpler solution?

---

### Post by sukwon0709 on 2006-04-27
Hi, I seemed to have same problem but I am using the wireless by typing:
sudo ifup eth0.
If works great but only bad thing is that I had to do this everytime I reboot the computer...lol

---

