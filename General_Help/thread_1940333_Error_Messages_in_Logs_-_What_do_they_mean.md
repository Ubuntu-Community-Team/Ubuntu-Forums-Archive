---
title: "Error Messages in Logs - What do they mean?"
date: 2012-03-13
forum: General Help
---

### Post by KevinM2k on 2012-03-13
Hi,

We are running Ubuntu Server 10.04 LTS. We have a number of cronjobs that should be running but for some reason they aren't, so I have tried to look for some kind of log that may tell us why, while I was doing this I have found /var/log/messages which has these 8/9 lines repeated every 30 seconds:

Mar 13 16:04:34 192.168.1.1 Vigor: [ARP][Arp address mismatch - Ethernet destination address doesn't match ARP target adress]
Mar 13 16:05:42 192.168.1.1 Vigor: last message repeated 2 times
Mar 13 16:06:01 192.168.1.1 Vigor: statistic: WAN1: Tx 0 Kbps, Rx 0 Kbps (5 min average)
Mar 13 16:06:01 192.168.1.1 Vigor: statistic: WAN2: Tx 614 Kbps, Rx 478 Kbps (5 min average)
Mar 13 16:06:01 192.168.1.1 Vigor: statistic: Session Usage: 498 (5 min average)
Mar 13 16:06:05 192.168.1.1 Vigor: [ARP][Arp address mismatch - Ethernet destination address doesn't match ARP target adress]
Mar 13 16:06:32 192.168.1.1 Vigor: DSL:  DSL Rebooting...#004
Mar 13 16:06:35 192.168.1.1 Vigor: [ARP][Arp address mismatch - Ethernet destination address doesn't match ARP target adress]

I understand what it is saying, but I have no idea how I am meant to fix this, can anyone help??

While you are there, do you know where the cron logs are I have looked at /var/log/cron and it doesn't exist.

Thanks

Kevin

---

