---
title: "[URGENT] Ubuntu 10.10 x64, server PC freezes randomly!"
date: 2011-02-11
forum: General Help
---

### Post by newn on 2011-02-11
Hi.
I'm having serious problems with the server I have...
I've installed a server edition of Ubuntu 10.10 x64 edition a few days ago. It freezes randomly. You can operate, if you are IN the server trough SSH already, tried top and nload commands during that time. Everything seems normal. But if I turn off SSH and try to connect trough SFTP or SSH, then it doesn't connect. Like no connection... Which means it's not a connection problem.
I turned on some server, which FPS can be measured, it was almost constant, as it should be during that period of time, which probably rules out the CPU problem.

Maybe I need to configure something for that PC or install something, or do something else? I've installed Linux first time, not counting Mint, so I don't know much about Linux yet...
Here's the configuration:

> Intel Processor:    Intel® Core&#8482; i3-550, 2x2x3.2Ghz
RAM memory:    4 GB ECC DDRIII
Hard drive:    RAID1 2x SATA2 1.5TB 7200RPM
Raid array:    Integrated SATA2 RAID levels 0/1/5/10
Disk bay:    Hotswap
Server platform:    Intel components> Disk /dev/sda: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0008ddef

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      180961  1453564928   83  Linux
/dev/sda2          180961      182402    11571201    5  Extended
/dev/sda5          180961      182402    11571200   82  Linux swap / Solaris

Disk /dev/sdb: 1500.3 GB, 1500301910016 bytes
255 heads, 63 sectors/track, 182401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000668d5
I've formatted HDD as / 50GB, 700GB /home, 700GB /root and 50GB swap.

I only noticed this because I let my friend host few of his game servers, while I'm making a program on my own PC. Paid for server PC before I did my work, because that was the last one, they are out of stock now, so I'd have to buy another or from other company.

Really need help with this one, as freezes aren't good. And I don't have graphical nor physical access to the PC. I have SSH console and could get a KVM device connected.
Thanks.

---

