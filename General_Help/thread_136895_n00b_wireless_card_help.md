---
title: "n00b wireless card help"
date: 2006-02-26
forum: General Help
---

### Post by mobi on 2006-02-26
Hello,

I am a total noobie to ubuntu.  I have attempted to install it in the past but could not get it to work.  I just downloaded the iso of 5.10 and it installed fine.  I have installed it on a dell c610, and the ethernet port works perfectly.  My problem is my linksys wpc11 v4 card.  The power light is on, it is displayed in the device manager list, and it appears that the drivers are there.  I cannot get it to connect to my wireless router.  I have read several articles and tried for several hours, but to no avail.  I did download ndiswrapper and I believe it ran\installed, but not sure where to go from here.  I am a windows pwr user and this is my first attempt at ubuntu.  I know nothing about linux, but I am willing and want to learn.  If there is any site or documentation that you guys\gals would recommend I would greatly appreciate it.  Also, is there a wireless network utility, like in windows, that manages the card and network profiles?  Really new to this and I apologize for being totally lost.  I hate to give up on ubuntu but if I cant get my wireless card working I may.  Again, any help would be awesome!

Thanks,

mobi

---

### Post by jamesr on 2006-02-26
Goto the console prompt and enter the following commands:-

sudo ifconfig -a
lspci
sudo iwconfig

and the post the outputs.

---

### Post by mobi on 2006-02-26
Jim,

Thanks for the quick reply.  this is what is at the bottom:

sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

sit0      no wireless extensions.

---

### Post by jamesr on 2006-02-26
Could you also post the other outputs, Please.

---

### Post by mobi on 2006-02-27
Jim, 

Here is the rest.



sudo ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:06:5B:36:DF:16
          inet addr:10.121.4.12  Bcast:10.121.4.255  Mask:255.255.255.0
          inet6 addr: fe80::206:5bff:fe36:df16/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19485 errors:0 dropped:0 overruns:1 frame:0
          TX packets:9260 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:19811080 (18.8 MiB)  TX bytes:772465 (754.3 KiB)
          Interrupt:11 Base address:0xec80

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:21825 errors:0 dropped:0 overruns:0 frame:0
          TX packets:21825 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:1645353 (1.5 MiB)  TX bytes:1645353 (1.5 MiB)

sit0      Link encap:IPv6-in-IPv4
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

mobi@ubuntu-m:~$ lspci
0000:00:00.0 Host bridge: Intel Corp. 82830 830 Chipset Host Bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corp. 82830 830 Chipset AGP Bridge (rev 02)
0000:00:1d.0 USB Controller: Intel Corp. 82801CA/CAM USB (Hub #1) (rev 01)
0000:00:1e.0 PCI bridge: Intel Corp. 82801 PCI Bridge (rev 41)
0000:00:1f.0 ISA bridge: Intel Corp. 82801CAM ISA Bridge (LPC) (rev 01)
0000:00:1f.1 IDE interface: Intel Corp. 82801CAM IDE U100 (rev 01)
0000:00:1f.5 Multimedia audio controller: Intel Corp. 82801CA/CAM AC'97 Audio Controller (rev 01)
0000:00:1f.6 Modem: Intel Corp. 82801CA/CAM AC'97 Modem Controller (rev 01)
0000:01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M6 LY
0000:02:00.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
0000:02:01.0 CardBus bridge: Texas Instruments PCI1420
0000:02:01.1 CardBus bridge: Texas Instruments PCI1420
0000:07:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8180L 802.11b MAC (rev 20)

---

