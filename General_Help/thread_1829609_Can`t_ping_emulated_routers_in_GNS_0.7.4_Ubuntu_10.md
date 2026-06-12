---
title: "Can`t ping emulated routers in GNS 0.7.4 Ubuntu 10.04"
date: 2011-08-20
forum: General Help
---

### Post by bisdjem on 2011-08-20
Hello!
I`m using GNS3 v 0.7.4 under Ubuntu 10.04 to emulate Cisco devices. I face a problem no communication between emulated devices. Currently I have two routers configured and ping between them doesn`t work.
Part of log file:
[FONT=Courier New]Aug 20 22:14:53.911 CPU0: PCI: read request at pc=0x60603f34: bus=0,device=7,function=0,reg=0x00
Aug 20 22:14:53.911 CPU0: PCI: read request at pc=0x60603f38: bus=0,device=7,function=0,reg=0x00
Aug 20 22:14:53.911 CPU0: PCI: write request (data=0x00004000) at pc=0x60603df0: bus=0,device=7,funct
ion=0,reg=0x0c
Aug 20 22:14:53.911 CPU0: PCI: write request (data=0x00004000) at pc=0x60603dfc: bus=0,device=7,funct
ion=0,reg=0x0c
Aug 20 22:14:53.919 Leopard-2FE(0): fetching init block at address 0x07bf4880
Aug 20 22:14:53.919 Leopard-2FE(0): rx_ring = 0x07bf48e0 (64), tx_ring = 0x07bf4d20 (128)
Aug 20 22:14:53.919 Leopard-2FE(0): CSR0 = 0x0101
Aug 20 22:14:53.971 CPU0: IO_FPGA: write to unknown addr 0x10002, value=0x0, pc=0x605f753c (size=2)
Aug 20 22:14:53.974 Leopard-2FE(0): fetching init block at address 0x07ba5b60
Aug 20 22:14:53.974 Leopard-2FE(0): rx_ring = 0x07ba5bc0 (64), tx_ring = 0x07ba6000 (128)
Aug 20 22:14:53.974 Leopard-2FE(0): CSR0 = 0x0101
Aug 20 22:14:53.975 Leopard-2FE(0): fetching init block at address 0x07bf4880
Aug 20 22:14:53.975 Leopard-2FE(0): rx_ring = 0x07bf48e0 (64), tx_ring = 0x07bf4d20 (128)
Aug 20 22:14:53.975 Leopard-2FE(0): CSR0 = 0x0101
Aug 20 22:14:54.069 CPU0: JIT: partial JIT flush (count=811)
Aug 20 22:14:54.142 Leopard-2FE(0): fetching init block at address 0x07ba5b60
Aug 20 22:14:54.142 Leopard-2FE(0): rx_ring = 0x07ba5bc0 (64), tx_ring = 0x07ba6000 (128)
Aug 20 22:14:54.142 Leopard-2FE(0): CSR0 = 0x0101

 Aug 20 22:17:23.101 CPU0: JIT: flushing data structures (compiled pages=1000)
Aug 20 22:17:27.686 Leopard-2FE(0): fetching init block at address 0x07ba5b60
Aug 20 22:17:27.686 Leopard-2FE(0): rx_ring = 0x07ba5bc0 (64), tx_ring = 0x07ba6000 (128)
Aug 20 22:17:27.686 Leopard-2FE(0): CSR0 = 0x0101
Aug 20 22:17:27.726 Leopard-2FE(0): am79c971_handle_txring: 1st desc: tmd[0]=0x7c50602, tmd[1]=0x8300fea8, tmd[2]=0x0, tmd[3]=0x0
Aug 20 22:17:27.726 Leopard-2FE(0): am79c971_handle_txring: loop: tmd[0]=0x7c50602, tmd[1]=0x8300fea8, tmd[2]=0x0, tmd[3]=0x0
Aug 20 22:17:27.726 Leopard-2FE(0): sending packet of 344 bytes
Aug 20 22:17:27.765 Leopard-2FE(0): am79c971_handle_txring: 1st desc: tmd[0]=0x7a0020a, tmd[1]=0x8300 ffc4, tmd[2]=0x0, tmd[3]=0x0
[B]Aug 20 22:17:27.765 Leopard-2FE(0): am79c971_handle_txring: loop: tmd[0]=0x7a0020a, tmd[1]=0x8300ffc4, tmd[2]=0x0, tmd[3]=0x0
Aug 20 22:17:27.765 Leopard-2FE(0): sending packet of 60 bytes[/B]
**Aug 20 22:17:27.768 Leopard-2FE(0): am79c971_handle_txring: 1st desc: tmd[0]=0x7c435ea, tmd[1]=0x8300 ffc4, tmd[2]=0x0, tmd[3]=0x0**
Aug 20 22:17:27.768 Leopard-2FE(0): am79c971_handle_txring: loop: tmd[0]=0x7c435ea, tmd[1]=0x8300ffc4, tmd[2]=0x0, tmd[3]=0x0[/FONT]
Marked line continually repeated.
Linux 2.6.32-33-generic #72-Ubuntu SMP Fri Jul 29 21:08:37 UTC 2011 i686 GNU/Linux
GNS3 v 0.7.4
Screen shot in attachment.
Please help! Many Thanks!

---

### Post by robertrose6 on 2011-08-20
do you have a default route set?

ip route 0.0.0.0 fa0/0 (both routers)

I think

---

### Post by bisdjem on 2011-08-21
Thanks for the answer.
Default gateway is not needed, routers belong to the same subnet. I notice a problem on layer 2:

[FONT=Courier New]Router#ping 10.10.10.2

Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.10.10.2, timeout is 2 seconds:
.....
Success rate is 0 percent (0/5)
Router#sh arp         
Protocol  Address          Age (min)  Hardware Addr   Type   Interface
Internet  10.10.10.2              0   Incomplete      ARPA   
Internet  10.10.10.3              -   cc01.4fc6.0000  ARPA   FastEthernet0/0
Router#[/FONT]

---

