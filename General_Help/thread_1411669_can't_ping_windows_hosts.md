---
title: "can't ping windows hosts??"
date: 2010-02-20
forum: General Help
---

### Post by axel_2078 on 2010-02-20
I noticed an odd problem last night.  I can’t ping or subsequently establish a RDP connection to XP SP3 machines on my network from my Ubuntu 9.04 laptop.  I tried last night and although it does resolve the computer name to it’s correct IP address (static entries on the firewall), I just get “destination host unreachable.”  However, I can ping my Unix-based NAS and my iMac successfully, as well as a FreeNAS virtual machine that I created a while back for testing.  Neither my XP SP3 virtual machine or my daughter’s desktop running XP SP3 will respond to pings from Ubuntu.  They will, however, respond to pings from my wife’s Vista laptop.  At first I thought it might be related to the Windows Firewall or SP3 because I was able to RDP into my daughter’s XP machine from my laptop just fine before I put SP3 on it (I was reinstalling the OS).  If it was the Windows firewall or SP3, I don’t understand why I can ping them and establish a RDP session to them both from my wife’s Vista laptop, but not my Ubuntu laptop.  That doesn’t make any sense to me.

---

