---
title: "mobile broadband slow in lucid with huawei e166"
date: 2010-05-03
forum: General Help
---

### Post by Hugo Alvarado on 2010-05-03
Hello , I seem to have a problem with my mobile broadband connection. I have a huaweii e166 usb hsdpa modem. It is veeerrryy slow.  It used to work fine in karmic a few days ago, used to get 800kbps (from whatismy.com), now in Lucid the speed test does not even finish sometimes, but if I open the system monitor it shows about 1kbps. Sometimes is gets slightly faster and I can browser a bit more, but then the speed goes down again, to barely useable. I have also setup the modem in xp and whatismy.com speedtest shows 900+kbps constantly. I did a clean install of lucid on my compaq presario cq60 laptop.

Any help/tips are appreciated. Thank you.

I have disabled ipv6 and installed the usb-modeswitch_1.1.2-2_i386.deb and usb-modeswitch-data_20100127-1_all.beb but it is still very slow.


lsusb:
Bus 008 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem


ifconfig:
ppp0      Link encap : Point-to-Point Protocol  
          inet addr:10.189.149.226  P-t-P:10.64.64.64  Mask:255.255.255.255
          UP POINTOPOINT RUNNING NOARP MULTICAST  MTU:1500  Metric:1
          RX packets:12909 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13229 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:3 
          RX bytes:3289181 (3.2 MB)  TX bytes:719515 (719.5 KB)



option: v0.7.2:USB Driver for GSM modems

---

### Post by Hugo Alvarado on 2010-05-04
So I tried again this morning, it is working waaayy better. whatismy.com speed test shows 1.01 Mbps, so far its been pretty constant.

I used usb_modeswitch to reset my modem, then tried connecting again and it works now. To reset:
```

sudo usb_modeswitch -v 0x12d1 -p 1001 -R -W

```

This might work for you, it seems to be ok now here.


[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509547](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/509547)

Download these 2 .debs
usb-modeswitch-data_20100127-1_all.deb
usb-modeswitch_1.1.0-2_i386.deb

Install them and then setup your modem via 'edit connections'. 

Some people use chap, some use pap. I tried both, I'm using chap right now.


I also use umtsmon, from [http://umtsmon.sourceforge.net/downloads.shtml](http://umtsmon.sourceforge.net/downloads.shtml) to show my reception ant other info, pretty handy.
"umtsmon is a tool to handle UMTS (3G) devices in Linux."


Good luck.

---

### Post by spiritumsantorini on 2010-05-04
Sorry, i dont understand.. How about the other model of the modem?

---

### Post by Hugo Alvarado on 2010-05-05
There is only one modem. The modem itself says "huaweii e166" on it, but lsusb says its a "Huawei Technologies Co., Ltd. E620 USB Modem".

This is the one I have: [http://www.alibaba.com/product-gs/264578718/huawei_e166_hsdpa_usb_modem.html](http://www.alibaba.com/product-gs/264578718/huawei_e166_hsdpa_usb_modem.html)

---

### Post by Hugo Alvarado on 2010-05-06
Update:
I now think that apt-zeroconf and my disabling of ipv6 was part of the problem, at least with the slow aptitude update. apt-zeroconf does not like if ipv6 is disabled. After re-enabling ipv6 by removing

#disable ipv6
net.ipv6.conf.all.disable_ipv6 = 1
net.ipv6.conf.default.disable_ipv6 = 1
net.ipv6.conf.lo.disable_ipv6 = 1

from /etc/sysctl.conf running aptitude update works better.

---

