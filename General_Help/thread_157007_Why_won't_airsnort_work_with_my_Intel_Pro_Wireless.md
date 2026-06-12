---
title: "Why won't airsnort work with my Intel Pro Wireless 2200BG?"
date: 2006-04-08
forum: General Help
---

### Post by wbastien on 2006-04-08
I have my IPW2200bg properly set up with WPA and everything but if I try to run airsnort, it doesn't see any packets coming through? I changed the chanel to the same as the network and still nothing. Is this a common thing or is there an alternative to airsnort?

---

### Post by voltaire961 on 2008-02-12
dearest friend, the intel pro 2200 BG won't work in airsnort nor in any other software for wep cracking cause there is no driver to support the monitor mode , u have to put the wireless card in  monitor mode in order to use the wep cracking software and the intel 2200 BG is not ready for it , although u can use another linux driver, try to search for updated linux driver for the IPW 2200 B/G  i think u can find, or u can just download the auditor knoppix no ipw 2100 that supports the IPW 2200 BG i repeat the auditor knoppix no ipw 2100
good luck

---

### Post by hahahan on 2008-02-12
Hm, IPW2200 here with driver shipped with 7.10 monitor mode works just fine.

root@satelite:/home/han# airmon-ng start eth1


Interface       Chipset         Driver

eth1            Centrino b/g    ipw2200 (monitor mode enabled)
wlan0           RTL8187         r8187

Rawtx is not supported, I don't know airsnort does need rawtx.

---

### Post by hahahan on 2008-02-12
Also installed airsnort. It works fine after choosing 'Other' in de driver menu and put the nic into monitor manually. So ipw2200 should not be a problem.

Regards.

---

### Post by sufslnd on 2008-03-15
How do I set my card into monitor mode manually?

---

