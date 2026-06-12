---
title: "Setting up your Compaq CQ40 for 9.10 Karmic Koala (Wireless &amp; Compiz)"
date: 2010-02-22
forum: General Help
---

### Post by HoXY on 2010-02-22
Ok this guide is for newbies that have just installed karmic onto their compaq presario cq40 or the likes of it. The general specs of the laptop should be like this:[INDENT]- AMD Athlon X2 Dual-Core 
- ATI Radeon HD 3200 Graphics shared
- 802.11b/g Broadcom Wireless
- HDD, RAM, etc
[/INDENT]The main problem with your unit should be the absence of the wireless card driver and your ATI graphic card driver. To solve both problems you should[INDENT]
[LIST=1]
[*]Enable the restricted drivers from SYSTEM>ADMINISTRATION>SOFTWARE SOURCES. Make sure the 'Proprietary drivers..' and 'Software restricted by..' under the UBUNTU SOFTWARE tab are checked. Under OTHER SOFTWARE tab, check the boxes for both the archive.canonical.com
[*] Then open your terminal and enter > sudo apt-get install bcmwl-kernel-source For those not interested in enabling Compiz can proceed to restarting their laptop for this should have solve your wireless problem already.
[*]Now to install Compiz, i suggest dl-ing & installing Envy. Find your driver under SYSTEM>ADMINISTRATION>HARDWARE DRIVERS and install it. Restart your unit and under Appearance Preferences>Visual Effects select Custom. Oh btw Compiz and Envy are available for download from synaptic or the Ubuntu Software Center under APPLICATIONS.
[/LIST]
[/INDENT]Hope this helps and have fun with your unit :D

---

