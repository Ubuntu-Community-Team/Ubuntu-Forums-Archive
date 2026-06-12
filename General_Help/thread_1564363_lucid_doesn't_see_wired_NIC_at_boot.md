---
title: "lucid doesn't see wired NIC at boot"
date: 2010-08-30
forum: General Help
---

### Post by Don Bowen on 2010-08-30
Dear Friends,
   Has anyone else ever booted and found that Ubuntu doesn't recognize the wired NIC port?   Lucid behaves as if the port doesn't exist.  
The only fix I've found is to reboot and cross your fingers and hope that Lucid can find it the next time.  That works irregularly.
I've seen this on several machines, not just one.
Anyone know a fix for this?  If so, please post it here.
thank you,

---

### Post by Don Bowen on 2010-09-01
anyone see this?  It seems to happen mostly on Dell notebooks.

---

### Post by plucky on 2010-09-02
Basic network troubleshooting:-
From a terminal ```
lspci
ifconfig
``` will tell you whether the interface is being seen.

It could possibly be that the network-manager hasn't started.To start the service ```
sudo service networking start
``` again from a terminal.

> Lucid behaves as if the port doesn't exist. 


Please expand on this statement


Good Luck

---

### Post by Morrighu on 2011-09-27
lspci shows all 4 of the network interfaces, however ifconfig shows nothing but the loopback (lo) :/.  I had two and I've even added two more but ifconfig still shows nada.  When I issue the command:  service networking start I get service networking stop/waiting.  And then nothing at all happens, so the network manager definitely isn't starting properly.

---

