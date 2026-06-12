---
title: "Terminal Server Client really slow when running RDPv5 over VPN"
date: 2010-10-08
forum: General Help
---

### Post by nmyrick on 2010-10-08
I couldn't find any post that directly relates to my issue, so I'm going to go ahead and post this.

I have Ubuntu 10.04 with Windows XP Pro installed in VirtualBox.  When I try to connect to Windows Servers using tsclient over a VPN with RDP or RDPv5, it is REALLY SLOW. 

However, on the same machine, I can go into the XP Virtual Machine and connect through the VPN and use Remote Desktop Connection with all settings set to default, except that I am using encryption, and it is very fast, so it is obviously not my connection.  What do I need to do to fix the Ubuntu tsclient? 

As far as I can tell, all the settings are the same on my tsclient as they are on XP Remote Desktop Connection, and I have tried adjusting just about every setting available in both tsclient and VPN connection, and I still have the same problem.

---

### Post by nmyrick on 2010-10-14
Bump

---

### Post by pricetech on 2010-10-14
Can you test it outside the VPN ??  Not that this is a lot of help, but i suspect the VPN is your problem since I connect to windows boxen using Terminal Server Client on a regular basis and it always outperforms Remote Desktop under windows.

---

### Post by Refalm on 2010-10-14
You can try to deactivate "bitmap caching". There have been problems reported with that feature in several bug reports.

---

### Post by nmyrick on 2010-10-17
I will try making sure the bitmap caching is disabled next time I use that VPN.  I would think that if it were an issue with the VPN, the Windows Remote Desktop would not perform well either.  

My experience has been that Ubuntu Terminal Services performs better than Windows Remote Desktop as long as I am on the internal network,  but on this VPN, Windows Remote Desktop performs better.

---

