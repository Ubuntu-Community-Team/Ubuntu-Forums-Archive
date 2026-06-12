---
title: "Wireless Help Please"
date: 2009-08-03
forum: General Help
---

### Post by tad214 on 2009-08-03
[B]Hello,
I just upgraded my 8.04, to 8.10, so i can upgrade to 9.0. I was told i could not just upgrade from 04 to 9. Anyway, hat is not a problem. The problem is, when i upgraded to 8.10, i now have no wireless options. When i click on my little network windows in the task bar, the drop down has all the options i need, however, they are greyed out. The only option that can be clicked on, is the vpn configuration. I need my plain old wireless network, with my plain old wireless network card. I won't to finish updating to 9.0 but i can't get online with it. Thanks in advance for the help. Have a blessed day. *[COLOR="Red"]Dale[/COLOR]* [/B]

---

### Post by Locutus_of_Borg on 2009-08-03
output of:```
lspci
iwconfig
```
please

---

### Post by tad214 on 2009-08-03
**Thank you. But i am new to ubuntu, so could you elaborate please? Thanks again for the quick reply. Dale**

---

### Post by Locutus_of_Borg on 2009-08-03
Click on Applications, then Accessories, then Terminal.

In the terminal window, first become root by entering the following text```
sudo -i
```
you will then need to supply your password
after entering your password enter the following text```
lspci
``` press enter, and highlight the resulting text with your mouse, left click and select copy, then post that into a reply here, do the same with the command ```
iwconfig
``` in the same terminal window, finally, type "exit" (without quotes) and press enter to drop the root privileges

---

### Post by tad214 on 2009-08-03
**Thank you very much. The battery on that laptop has died, so i want be able to charge it till i get home. I will get that done later on tonight, and get it posted here for you to see. Thanks again Dale**

---

### Post by tad214 on 2009-08-04
[B]Hi Guys,
I ran them commands you told me to, and here are the results:

*[COLOR="Red"]For command lspci[/COLOR]*:

00:00.0 Host bridge: Intel Corporation 82855PM Processor to I/O Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation 82855PM Processor to AGP Controller (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
USB UHCI
Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
USB UHCI
Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
USB UHCI
Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4M)
USB2 EHCI Controller
(rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4M)
LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4M)
IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4L/
ICH4M)
AC'97 Modem
Controller (rev 01)
01:00.0 VGA compatible controller: nVidia Corporation NV34M [GeForce FX Go5200 64M] (rev a1)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401 100BaseT
(rev 01)
02:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
02:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE1394
Controller
02:03.0 Network controller: Intel Corporation PRO/Wireless 2200BG [Calexico2] Network Connection
(rev 05)

*[COLOR="red"]For command iwconfig[/COLOR]*:

root@dalelaptop:~#
iwconfig
lo no wireless extensions.
eth0 no wireless extensions.
eth1 unassociated ESSID:"cheers wireless"
Mode:Managed Channel=0 Access Point: NotAssociated
Bit Rate:0 kb/s TxPower=
20 dBm Sensitivity=8/0
Retry limit:7 RTS thr:off Fragment thr:off
Encryption key:off
Power Management:off
Link Quality:0 Signal level:0 Noise level:0
Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
Tx excessive retries:0 Invalid misc:0 Missed beacon:0
pan0 no wireless extensions.
root@dalelaptop:~#

Thank you again for all the help. *[COLOR="red"]Dale[/COLOR]*[/B]

---

### Post by tad214 on 2009-08-04
**Is anyone there that cann assist me please?**

---

### Post by tad214 on 2009-08-04
**Bump!!!!! Please can someone help me? I thought this forum had linux pro's on it to assist the people that are not. Do i need to place this somewhere else on this site? Thanks for any help in advance. *[COLOR="Red"]Dale[/COLOR]***

---

### Post by BslBryan on 2009-08-04
Dale, 

Try this.  Perhaps your wireless card is not being detected.

```
sudo rmmod ssb
sudo modprobe wl
```

Wait about 5 minutes and then try again to connect.

---

### Post by tad214 on 2009-08-04
[B]Thanks for the reply bsl. The first command told me this:
ERROR: Module ssb is in use by b44.

The second command did nothing at all, just sent me back to my root prompt. Now what?[/B]

---

### Post by tad214 on 2009-08-04
**Is there anybody else that can help me?**

---

### Post by BslBryan on 2009-08-04
Perhaps this thread will help you. :-)

[http://ubuntuforums.org/showthread.php?t=965837](http://ubuntuforums.org/showthread.php?t=965837)

It seems to be exactly what you're looking for, the same hardware and everything.

---

### Post by tad214 on 2009-08-04
**Thank you. I will see what i can do. thanks again. I will let you know one way or the other. Dale**

---

### Post by Locutus_of_Borg on 2009-08-04
dale, the output of the iwconfig command shows that your wireless is in fact working and is associated with the wireless network "cheers wireless"

enter the following in a terminal, one line at a time supplying your password after the first:```
sudo -i
ifconfig eth1 down
dhclient -r eth1
ifconfig eth1 up
iwlist eth1 scan
```

after the last command you should get a list of all available wireless networks

choose one of them and take note of what it lists is the ESSID

for example, the output will have entries that look like the following: ```
Cell 01 - Address: 00:12:17:7E:95:8B
                    Channel:6                 
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-42 dBm  
                    Encryption key:off                   
                    ESSID:"Library"           
```
In the above case the network name is "Library"

once you have this information you can tell your card to connect to that network by issuing the following commands into the same terminal as above:
```
iwconfig eth1 essid Library
dhclient eth1
```

wait a few moments and you should get a message that you have been "bound to 192.168.0.1" or some similar address, following this message, in that same terminal enter the following line```
ping 74.125.45.100
``` if you get a response, you are successfully connected, if after this you still cannot connect to anything with firefox, then the problem is with your dns settings,
 
you can fix this by editing the file /etc/resolv.conf and putting in the address of the router you are connected to, the output of the dhclient command from above will have told you the address of the router (the bound to "#" is the address)
```
gksudo gedit /etc/resolv.conf
```
enter that into a terminal and a text editor will open up, erase the contents of this file and paste this into it:
```

nameserver 192.168.0.1

```
replace 192.168.0.1 with the address that dhclient reported you were bound to.  

you should now be able to use the internet through firefox and such

---

### Post by tad214 on 2009-08-05
Hi Guys,
**I will try all this and see what happens. I have been doing various things, so i m working on this in between doing other things. I will let you guys know if this works. Can you tell me what the actual problem is? Like i sais, before i upgraded to 8.10 on my way 2 9.0, everything was working great. I could click on the little monitor windows in the task bar, and one of the options that was there was, other networks, or something like that. Anyway, all the options are still there, however, they are greyed out where i can not click on them. Thanks again for all the great help guys. Dale P.S. I should have just downloaded an image of th newest one, and jsu do a clean install and everything would be great. If you would though, so i can learn about this stuff, enlighten me on what exactely went wrong and how? Thanks again. Dale**

---

