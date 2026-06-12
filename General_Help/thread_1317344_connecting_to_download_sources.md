---
title: "connecting to download sources"
date: 2009-11-06
forum: General Help
---

### Post by madScientist3 on 2009-11-06
Hi all,

After upgrading to Karmic I got the wireless going fine and internet is going strong after disabling ipv6 (my router doesnt support it and it was causing very slow internet). However there are two issues that I cannot fix.

In order to do any downloads via apt-get install, update manager and synaptic I have to go to software sources, choose other and get it to find the best server (usually one of two good New Zealand sites), then close and do install. This will work for everything but adobe flash and only for about 2 mins when I have to go back to software sources again. My internet is ok during this process, no wireless dropout. Just an inability to find a connection. This I believe is causing the second issue of the Adobe flash failing to complete install, it hangs on connecting to canonical. So, I have no flash.
This is not just a wireless issue as I have the same problem when connected by LAN. Network access is fine also.

output from lspci

03:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)

Any help on this will be greatly appreciated
Cheers

---

