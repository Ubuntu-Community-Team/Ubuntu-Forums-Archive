---
title: "need help to activate my wireless network  device"
date: 2009-07-23
forum: General Help
---

### Post by crazymechanic on 2009-07-23
hi.
i am new with ubuntu (using 9.04 32bit) but problem is that i have an internet connection from one of our mobile network provider. it has only driver for XP and vista ....but with out an internet connection i just can't begin with my ubuntu.

can any one tell me how to install that device in ubuntu without an internet connection???

Device name: ZTE internet modem
Model: ZTE MG 880 USB modem
network: CDMA 1X

it has the following help note but i can't understand,,,,(beginner)

1, Load driver-zte evdo

1),Copy ztemt.ko from release's relevant directory to certain directory (take /home/lm/ztemt for example);
    e.g., you need install Fedora core 6:
       cp release/Fedora/FC6/ztemt.ko  /home/lm/ztemt/

2),cp us-test/wvdial-conf /etc/

3),Load driver
     insmod /home/lm/ztemt/ztemt.ko

4),Insert network card;

5),Run wvdial and to dial successfully (need root authorization). Normally, the following prompts will appear:
    --> pid of pppd: 2450
    --> Using interface ppp0
    --> Authentication (CHAP) started
    --> Authentication (CHAP) successful
    --> local  IP address 220.205.100.27
    --> remote IP address 220.192.56.19
    --> primary   DNS address 220.192.32.103
    --> secondary DNS address 220.192.0.130
    --> Script /etc/ppp/ip-up run successful
    --> Default route Ok.
    --> Nameserver (DNS) Ok.
    --> Connected... Press Ctrl-C to disconnect

6,FAQ
1),require software support:
     udev
     wvdial

2),It might not be able to resolve domain name after running wvdial to dial successfully. 
In this case, you need manually add primary DNS address and secondary DNS address to /etc/resolv.conf.

---

