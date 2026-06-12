---
title: "manual wifi configuration questions (I know boring boring boring ;)"
date: 2006-02-07
forum: General Help
---

### Post by stardotstar on 2006-02-07
In an ongoing attempt to find out why I am continuing to experience flaky wireless connections today and assuming that the standard network configurator was somehow conflicting with NetworkManager I uninstalled NM and proceeded to use only the configurator.  Things were still flaky and once I got home I decided to try and associate with my home essid manually to understand more about the nature of my problems...  (applying KISS if you like ;) )

I proceeded thus:

sudo iwconfig eth1 essid skink key s:xxxxxx

which rewarded me with:
```

eth1      Link encap:Ethernet  HWaddr 00:12:F0:35:4E:7E
          inet6 addr: fe80::212:f0ff:fe35:4e7e/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:64 (64.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Base address:0x6000 Memory:c0214000-c0214fff

```

and not knowing how to get iwconfig to pull a full dhcp address/dns set I issued:

wparker@geko:~$ sudo ifconfig eth1 192.168.0.101

and then finding my route faulty:

sudo route add default gw 192.168.0.1 eth1

which allowed me to come here and post :)

I notice my /etc/network/interfaces lists the dhcp type of association and I cant see in iwconfig man where dhcp and dns etc etc are stipulated?

Here is my other "flaky" router configuration that is saved for use at work in the absence of NM:

```

iface eth1 inet dhcp
wireless-essid Casper
wireless-key s:xxxxx

```

Can someone please enlighten me as to how to troubleshoot my wireless problems and issue the correct manual commands to progress my knowledge.

Will the standard configurator just find "skink" in the absence of "Casper" if I make another entry like that??  Or do I have to make another site?

BTW here is other stuff that is often asked for:

```

wparker@geko:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11g  ESSID:"skink"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:46:BD:49:16
          Bit Rate=54 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=72/100  Signal level=-56 dBm  Noise level=-79 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:6

sit0      no wireless extensions.

...lspci
0000:02:02.0 Network controller: Intel Corp. PRO/Wireless 2200BG (rev 05)
...lspci -n
0000:02:02.0 0280: 8086:4220 (rev 05)

wparker@geko:~$ modprobe -l | grep ipw
/lib/modules/2.6.12-10-386/kernel/drivers/usb/serial/ipw.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ipw2200/ipw2200.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ipw2100/ipw2100.ko
/lib/modules/2.6.12-10-386/kernel/drivers/net/wireless/ipw2100/fsam7400.ko

wparker@geko:~$ ndiswrapper -l
Installed ndis drivers:
w22n51  driver present, hardware present


hmmm.. what else?
```

---

