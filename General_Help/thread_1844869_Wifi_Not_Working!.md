---
title: "Wifi Not Working!"
date: 2011-09-15
forum: General Help
---

### Post by DeathByLinux on 2011-09-15
Hello,
        I just moved to a new place and they have wifi over here, but I cannot connect to it. I am typing from my friend's computer, who also lives in the same place. I looked at the password on his computer and I am confident that that is not the problem. 
I have WPA & WPA2 Personal selected and I checked my friend's computer and he has WPA2 selected on his Mac. Are there any other possibilities as to why this may not be working? Perhaps something in the Editing screen of Network Connections?
I can connect to other unprotected connections in the area no problem. Any help would be appreciated, since I am going to be living at this place and this could really dampen things.
-DeathbyLinux

---

### Post by bohemian9485 on 2011-09-15
The WiFi router probably has its Media Access Control (MAC) filter turned on, so even if you know the password your connection will still be rejected by the router. Ask the person who is managing the router to include your MAC on the list.

---

### Post by fdrake on 2011-09-15
can you post the results for these commands:
What the name of the essid you are trying to connect?
```

sudo lshw -c Network
sudo iwlist scan
nm-tool
wpa_supplicant -v
less /etc/NetworkManager/nm-system-settings.conf
ls /etc/NetworkManager/system-connections/

```

---

### Post by pqwoerituytrueiwoq on 2011-09-15
make sure yuo are usinghte correct password method (passphrase/key)

---

### Post by wildmanne39 on 2011-09-15
Also you may be able to connect by setting your router to wpa2 and not mixed mode because ubuntu does not like mixed mode depending on your card and driver.
Thank you

---

### Post by DeathByLinux on 2011-09-16
> **fdrake said:**
> can you post the results for these commands:
What the name of the essid you are trying to connect?
```

**sudo lshw -c Network**
sudo iwconfig list scan
nm-tool
wpa_supplicant -v
less /etc/NetworkManager/nm-system-settings.conf
ls /etc/NetworkManager/system-connections/

```

sudo lshw -c Network:

*-network               
       description: Ethernet interface
       product: 88E8040T PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 12
       serial: 00:1e:68:5d:c2:87
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 firmware=N/A latency=0 link=no multicast=yes port=twisted pair
       resources: irq:46 memory:81000000-81003fff ioport:6000(size=256)
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:08:00.0
       logical name: wlan0
       version: 01
       serial: 00:1b:9e:ef:5e:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-30-generic firmware=N/A ip=192.168.0.190 latency=0 link=yes multicast=yes wireless=IEEE 802.11abg
       resources: irq:17 memory:81400000-8140ffff
**sudo iwconfig list scan**
iwconfig: unknown command "scan"
**nm-tool**

NetworkManager Tool

State: connected

- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             unavailable
  Default:           no
  HW Address:        00:1E:68:5D:C2:87

  Capabilities:
    Carrier Detect:  yes

  Wired Properties
    Carrier:         off


- Device: wlan0  [Auto one tree hill] ------------------------------------------
  Type:              802.11 WiFi
  Driver:            ath5k
  State:             connected
  Default:           yes
  HW Address:        00:1B:9E:EF:5E:C8

  Capabilities:
    Speed:           1 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    Trail08:         Infra, 00:1E:58:01:5D:08, Freq 2417 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    HPD110a.55B797:  Ad-Hoc, 02:25:45:E7:89:E6, Freq 2437 MHz, Rate 54 Mb/s, Strength 61
    Gigaset9C3:      Infra, 00:18:D1:91:09:C8, Freq 2462 MHz, Rate 54 Mb/s, Strength 30 WEP
    loewen:          Infra, 0C:29:CD:28:42:EC, Freq 2412 MHz, Rate 54 Mb/s, Strength 21 WPA
    Ram:             Infra, A8:39:44:46:9F:10, Freq 2462 MHz, Rate 54 Mb/s, Strength 22 WPA WPA2
    Ameet-guest:     Infra, C0:C1:C0:58:FB:B9, Freq 2462 MHz, Rate 54 Mb/s, Strength 14
    Ameet:           Infra, C0:C1:C0:58:FB:B7, Freq 2462 MHz, Rate 54 Mb/s, Strength 12 WPA WPA2
    irodriguez:      Infra, 00:26:88:E9:02:B8, Freq 2412 MHz, Rate 54 Mb/s, Strength 17 WPA WPA2
    DNetwork:        Infra, 00:18:E7:CE:94:D0, Freq 2437 MHz, Rate 54 Mb/s, Strength 20 WPA
    mike:            Infra, 00:14:D1:3E:EF:68, Freq 2462 MHz, Rate 54 Mb/s, Strength 28 WPA
    LA Agency:       Infra, 00:1C:F0:C3:DD:8C, Freq 2447 MHz, Rate 54 Mb/s, Strength 28 WPA
    DIR-615-9647:    Infra, 02:25:45:E7:89:E6, Freq 2437 MHz, Rate 54 Mb/s, Strength 41 WPA WPA2
    DIR-615-9647:    Infra, 00:18:E7:C6:18:A2, Freq 2437 MHz, Rate 54 Mb/s, Strength 47 WPA WPA2
    Oreo:            Infra, 00:26:B8:EC:97:A4, Freq 2412 MHz, Rate 54 Mb/s, Strength 64 WPA WPA2
    *one tree hill:  Infra, 00:1C:F0:FC:22:D0, Freq 2442 MHz, Rate 54 Mb/s, Strength 24
    JKo:             Infra, 00:25:9C:4D:49:9F, Freq 2462 MHz, Rate 54 Mb/s, Strength 68 WPA

  IPv4 Settings:
    Address:         192.168.0.190
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.0.1

    DNS:             192.168.0.1
**wpa_supplicant -v**
wpa_supplicant v0.6.10
Copyright (c) 2003-2009, Jouni Malinen <j@w1.fi> and contributors
**less /etc/NetworkManager/nm-system-settings.conf**

# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false

~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
~
(END) 
**ls /etc/NetworkManager/system-connections/**
Nothing happens with this command.

---

### Post by wildmanne39 on 2011-09-16
Hi, one thing it looks like your mode is not managed and it should be.

Please run these commands one at a time.
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid “YOURESSID_IN_QUOTES”
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```
unplug your wired connection before you run these commands if you have one.

Also please post the results of these commands:
```
rfkill list all
```
```
dmesg | egrep 'ath|firm'
```
```
lsmod | grep ath
```
Thank you

---

### Post by DeathByLinux on 2011-09-16
> **wildmanne39 said:**
> Hi, one thing it looks like your mode is not managed and it should be.

Please run these commands one at a time.
```
sudo ifconfig wlan0 down
sudo dhclient -r wlan0
sudo ifconfig wlan0 up
sudo iwconfig wlan0 essid “YOURESSID_IN_QUOTES”
sudo iwconfig wlan0 mode Managed
sudo dhclient wlan0
```unplug your wired connection before you run these commands if you have one.

Also please post the results of these commands:
```
rfkill list all
``````
dmesg | egrep 'ath|firm'
``````
lsmod | grep ath
```Thank you

Is the ESSID the name of the network? For example, I am trying to connect to Oreo in that list that I gave to you at the top. Would I write "sudo iwconfig wlan0 essid 'Oreo'"?

---

### Post by wildmanne39 on 2011-09-16
Hi, it is the name of the network you want to connect too.
Thank you

---

### Post by DeathByLinux on 2011-09-16
**rfkill list all**
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

**dmesg | egrep 'ath|firm'**

[    0.614746] device-mapper: multipath: version 1.1.1 loaded
[    0.614749] device-mapper: multipath round-robin: version 1.0.0 loaded
[   12.446410] ath5k 0000:08:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   12.446425] ath5k 0000:08:00.0: setting latency timer to 64
[   12.446488] ath5k 0000:08:00.0: registered as 'phy0'
[   13.078146] ath: EEPROM regdomain: 0x69
[   13.078150] ath: EEPROM indicates we should expect a direct regpair map
[   13.078155] ath: Country alpha2 being used: 00
[   13.078157] ath: Regpair used: 0x69
[   13.109179] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa2, PHY: 0x61)

**lsmod | grep ath**

ath5k                 130083  0 
mac80211              231927  1 ath5k
ath                     8153  1 ath5k
cfg80211              144822  3 ath5k,mac80211,ath
led_class               2633  2 ath5k,sdhci





I would like to report that I got the wireless password of a neighbor's network and my computer is able to connect to it and 2 other unprotected networks near me. I asked this neighbor to try and log on to Oreo (the network that my landlord offers) and his computer reports that the password is wrong, EVEN though I got this password off of my landlord's computer. (I obtained the password by going into my landlord's network settings on his Mac and unveiled the password so I could be sure that he wasn't telling me the incorrect password.)
Could bohemians be right and could this be some sort of a security measure which only allows a select few computers to connect to the network or am I not making any sense?

P.S: Thanks to all who are engaged in trying to help me. This is a pretty big issue for me, as I have come to regard the internet as a basic necessity in my life. haha

---

### Post by wildmanne39 on 2011-09-16
Hi, I guess it is possible but the encryption of that network is set to wpa/wpa2 and it works better for ubuntu if it is just wpa2.
Thank you

---

### Post by DeathByLinux on 2011-09-17
How would I go about setting the encryption JUST to WPA2? (System>Preferences>Network Connections> and then???)

---

### Post by wildmanne39 on 2011-09-17
Hi, you have to plug your wired connection into the router then type this into the address bar 192.168.0.1 there may be a little different numbers for your router, then click on wireless in the router configuration settings and change encryption to wpa2.

If you do not have access to the router then I do not know what to tell you to do.
Thank you

---

### Post by cryptotheslow on 2011-09-17
Ask your landlord to check on the web interface of the router that it is set to allow new clients. Many wireless routers come with that switched off and need putting into an "accepting new clients" state for a new client to connect. This is sometimes done via the web interface and sometimes by pressing a button or combination of physical buttons on the router.


Edit - reading back this would seem to be the most likely cause. As you can connect fine to other open and encrypted access points - and your neighbour gets the same problem trying to connect to your landlord's router.

---

### Post by DeathByLinux on 2011-09-17
I am working on getting the password to this network and I will use my landlord's computer to access it and make the change. 
In the mean time, I was wondering if anything can be done to Linux to fix the problem.

---

### Post by wildmanne39 on 2011-09-17
Hi, not as far as I know you need to have his password and approval to access his network.
Thank you

---

### Post by cryptotheslow on 2011-09-19
> **DeathByLinux said:**
> I am working on getting the password to this network and I will use my landlord's computer to access it and make the change. 
In the mean time, I was wondering if anything can be done to Linux to fix the problem.


If the problem is that the router is set to not accept new clients unless instructed to, then no there is nothing you can do in Linux or any other OS for that matter to workaround it.

---

### Post by DeathByLinux on 2011-09-29
Alright guys, I just reset the router and it put the settings to something that Ubuntu can work with. Thanks for everyone's attempt to help out. :) 
-DeathbyLinux

---

### Post by wildmanne39 on 2011-09-29
Hi, that is great, I am, glad it is working, would you please go to the top of the page and mark this thread solved by clicking on thread tools. Thank you so much.

---

