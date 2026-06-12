---
title: "network card transmit timeout"
date: 2006-05-03
forum: General Help
---

### Post by adamruck on 2006-05-03
Hi,

This is my first post, and I would like to say Ubuntu is a great distro! 

My Setup.
-------------

I have an older/slower laptop. Its a VIA C3 processor and 256MB of ram. I am running  Ubuntu 5.10 without any of the updates installed.

A few things from lspci that might be helpful
--------------------------------------------------------

0000:00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
0000:01:00.0 VGA compatible controller: S3 Inc. 86C380 [ProSavageDDR K4M266] (rev 02)

0000:00:01.0 PCI bridge: VIA Technologies, Inc. VT8605 [PM133 AGP]

My problem
--------------

When my laptop is mostly idle, my network card works just fine. I can do all of my usual network things(ping, broadcastping, arping, telnet, ssl, http, etc). When my laptop is under load, none of those things work. Now when I say under load, I mean anything above about 50 percent processor usage. This problem is very consistant. I can start a continuous ping, and watch it timeout when firefox is loading, or switching tabs, or whatever. Then when firefox is done doing whatever, the ping starts working again. The same things happens when I run an intensive php script, or load a different program, or anything that causes load on the processor.

I get the following messages from dmesg(many times)
----------------------------------------------------
[4800250.403000] NETDEV WATCHDOG: eth0: transmit timed out
[4800250.403000] eth0: Transmit timeout, status 01 0000 0000 media 10.
[4800250.403000] eth0: Tx queue start entry 14  dirty entry 10.
[4800250.403000] eth0:  Tx descriptor 0 is 00002000.
[4800250.403000] eth0:  Tx descriptor 1 is 00002000.
[4800250.403000] eth0:  Tx descriptor 2 is 00002000. (queue head)
[4800250.403000] eth0:  Tx descriptor 3 is 00002000.
[4800250.403000] eth0: link up, 100Mbps, full-duplex, lpa 0x45E1


Other notes
---------------
I have never had this problem on the same laptop with different distros

Questions
------------
Whats up?
Driver problem?
Kernel problem?
Hardware problem?

---

### Post by jesterfred on 2008-01-07
I have a similar problem.  In my case I am using two PCI SMC NICs.  I receive the following only under extreme network loads going over a 100 Mbps link.  (NFS Mounted drive copying a DVD image.)

> Jan  7 21:13:42 griffin kernel: [43344876.430000] NETDEV WATCHDOG: eth0: transmit timed out
Jan  7 21:13:42 griffin kernel: [43344876.430000] eth0: Transmit timeout, status 0d 0000 c07f media 90.
Jan  7 21:13:42 griffin kernel: [43344876.430000] eth0: Tx queue start entry 67763  dirty entry 67759.
Jan  7 21:13:42 griffin kernel: [43344876.430000] eth0:  Tx descriptor 0 is 001e0424.
Jan  7 21:13:42 griffin kernel: [43344876.430000] eth0:  Tx descriptor 1 is 001e0424.
Jan  7 21:13:42 griffin kernel: [43344876.430000] eth0:  Tx descriptor 2 is 001e0424.
Jan  7 21:13:43 griffin kernel: [43344876.430000] eth0:  Tx descriptor 3 is 001e0424. (queue head)
Jan  7 21:13:43 griffin kernel: [43344876.430000] eth0: link up, 100Mbps, full-duplex, lpa 0xC5E1

The link does come back up after several seconds.

Reading on the net leads me to believe this problem is not related to a specific NIC, but rather to the Linux kernel under heavy load.  Some posts suggest this is a know bug and will be fixed in the 2.6.23 series.  I use Ubuntu 7.10.  I hope this problem is solved soon!

---

