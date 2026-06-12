---
title: "Wireless lan problem- is it getting worst? :/"
date: 2009-08-10
forum: General Help
---

### Post by Moichim on 2009-08-10
Hey everybody.
I am new to Ubuntu (9.04) and linux  :P and I am going in circles about how to set up my wireless PC card (trendnet tew-420pc) on my laptop (Thinkpad r51e). :confused:It was supposed to work out of the box according to wiki. I did get a few networks to show up on the top of the screen but it tried and tried to connect to no avail. (I am trying to get to a non secure, free, internet hotspot) 
I followed up very well all the fllowing thread to no avail too, and worst now: I dont even see networks at all ( [https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3AB1_(ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Device/TRENDnet_TEW-421PC_H/W%3AB1_%28ndiswrapper")) ) 
Lets see what I could post as an info on my system ?!:

betzaleldaniel@bina:~$ sudo iwconfig
[sudo] password for betzaleldaniel: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:eek:ff   Fragment thr=2352 B   
          Encryption key:eek:ff
          Power Management:eek:ff
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

ppp0      no wireless extensions.


 betzaleldaniel@bina:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Device 5a31 (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:04.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:06.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 11)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 02)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 02)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200M]
02:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5751F Fast Ethernet PCI Express (rev 21)
04:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8185 IEEE 802.11a/b/g Wireless LAN Controller (rev 20)


betzaleldaniel@bina:~$ sudo ifup <ath0>
bash: syntax error near unexpected token `newline'


PLEASE HEEEEEELP

---

### Post by P4man on 2009-08-10
I think you got that network card wrong. Your lspci output suggests a Realtek RTL-8185 based card, not a marvel based card for which you followed the ndiswrapper installation instructions?

Or are you using a USB wifi stick? In that case, please post output of lsusb

---

### Post by Commander_Keen on 2009-08-10
what kind of Wireless card are you using.
I'm using Netgear, 111 Version 2. 
It works. it has Wep, wep2 and wpa, wpa2 and a few others.
It worked out side of the box.
and if you go to geeks.com you can pick it up $10

---

### Post by Moichim on 2009-08-10
> **P4man said:**
> I think you got that network card wrong. Your lspci output suggests a Realtek RTL-8185 based card, not a marvel based card for which you followed the ndiswrapper installation instructions?

Or are you using a USB wifi stick? In that case, please post output of lsusb

SOLVED ! Thanks a lot...:P
By the way I didnt know I had to subscribe to a thread I post so I didnt know I got answers till now :/  I dont know what was the real issue but I worked it out after hours of messing up with ndiswrapper. ( i think I had to write ndswrapper in the module (whatever that is :/) which wasnt clear from the how to I followed and the driver may have been the wrong one so i tryed a different one like you said)
 Thanks a lot again...:P

---

### Post by P4man on 2009-08-10
ndiswrapper lets you install a windows driver. It "wraps" the driver so linux can use it. Its actually a last resort measure for a few wifi cards that linux can't support natively (usually because the manufacturer refuses to open up their specifications, and reverse engineering doesnt work well enough). 

Your card I think IS supported by the linux kernel and shouldn't need any ndiswrapper stuff, it should work straight out of the box. But hey, if you got it working someone.. if it aint broke, don't fix it i guesss :)

---

