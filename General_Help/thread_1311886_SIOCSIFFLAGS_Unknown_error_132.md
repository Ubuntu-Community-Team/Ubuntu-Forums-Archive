---
title: "SIOCSIFFLAGS: Unknown error 132"
date: 2009-11-02
forum: General Help
---

### Post by nicklausmichael on 2009-11-02
Im having issues with getting my wifi card in my laptop to work.. it was working last night but when I woke up this morning and powered up my laptop and tryed to use it I kept getting this error...```
c0ld@c0ld-laptop:~$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

``````
c0ld@c0ld-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```Chipset Information
```
wlan0        Atheros     ath5k - [phy0]

``````
c0ld@c0ld-laptop:~$ sudo dhclient
[sudo] password for c0ld: 
Internet Systems Consortium DHCP Client V3.1.2
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

SIOCSIFFLAGS: Unknown error 132
SIOCSIFFLAGS: Unknown error 132
Listening on LPF/wlan0/00:23:4d:0f:c4:57
Sending on   LPF/wlan0/00:23:4d:0f:c4:57
Listening on LPF/eth0/00:1d:72:72:c1:07
Sending on   LPF/eth0/00:1d:72:72:c1:07
Sending on   Socket/fallback
receive_packet failed on wlan0: Network is down
DHCPREQUEST of 192.168.0.187 on wlan0 to 255.255.255.255 port 67
send_packet: Network is down
DHCPREQUEST of 192.168.1.100 on eth0 to 255.255.255.255 port 67
DHCPACK of 192.168.1.100 from 192.168.1.1
bound to 192.168.1.100 -- renewal in 32900 seconds.
c0ld@c0ld-laptop:~$ 

```Any advice or suggestions on how to eliminate this issue is most appreciated..Ive researched all day and have yet to find a solution..Thank You!


SOLUTION:Using these commands fixed the issue...Just make sure you specify the drivers of your interface..
```

rmmod ath5k
rfkill block all
rfkill unblock all
modprobe ath5k
rfkill unblock all
ifconfig wlan0 up

```Sources:[html]http://www.mail-archive.com/ubuntu-bugs@lists.ubuntu.com/msg1813445.html[/html]Hope this helps any others out there with same issue!

LIKE TO STATE THIS SOLUTION ONLY WORKED 1 DAY FOR ME!! LOL SO IM STILL OPEN TO SUGGESTIONS ON WHAT TO DO.

---

### Post by Krogulec on 2009-11-04
Something from my experience:

23:39:25 <mr00wka@r2d2>[~] rfkill list
0: tpacpi_bluetooth_sw: Bluetooth[INDENT]    Soft blocked: yes
    Hard blocked: yes[/INDENT]<b>1: phy0: Wireless LAN[INDENT]    *Soft blocked: yes*
    Hard blocked: no[/INDENT]</b>


Now if I knew WHAT software is blocking this device I could probably disable it permanently. It might be the same in your case....  Anyhow, after running **rfkill unblock all** my wireless is working perfectly

---

### Post by robinPain on 2009-11-11
Thanks very much!!! 

After two days messing about, "rfkill unblock all" worked for  me (you need to do it after every start up).

Now both:-
Ralink rt2501usb
Netgear rtl8187

have both started working on 9.10 (they both work out-of-the-box on 9.04)

---

### Post by kinley3 on 2009-11-24
This didn't work for me. Still showing as disabled.

Using Broadcom4318. I think this might be the Satan of wireless cards after trying for the past day to figure this out.

EDIT:
It's showing up under *-network:1 as opposed to wlan0...could this be an issue? Also the driver is listed as b43-pci-bridge but it's not a PCI card...

---

### Post by pippo_73 on 2010-01-26
Any news on how to find a solutions to this problem?

---

### Post by &lt;hidden&gt; on 2010-04-01
Demn... So many stupid replies to all the related bug-reports and everybody saying it's not my falt/It's not my problem/It's BIOS problem/It's wicd problem/It's NetworkManager problem/It's b43-fwcutter/Blah Blah Blah

The only real solution is on **Russian Site**, of course, where else...
**[&#1056;&#1077;&#1096;&#1077;&#1085;&#1080;&#1077; &#1087;&#1088;&#1086;&#1073;&#1083;&#1077;&#1084; &#1089; WiFi &#1074; Ubuntu 9.10 (SIOCSIFFLAGS: Unknown error 132)]("http://www.opennet.ru/tips/info/2214.shtml")** 
(Troubleshooting WiFi in Ubuntu 9.10)
If steps are not obvious then translate.google.com ;)

---

