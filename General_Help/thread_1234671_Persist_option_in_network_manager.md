---
title: "Persist option in network manager"
date: 2009-08-08
forum: General Help
---

### Post by shutdown on 2009-08-08
My problem is that I need to re-connect to my pppoe connection if the line is dropped . I noticed that there is a persist option on pppoeconf and since nm apprently uses pon and poff for its connecting , where can i find the connection settings for the connection i have set up using network manager and put the persist setting to true . 

Or is there any other way of reconnecting if and when the line is dropped ? 

Thanks , 
Jit

---

### Post by shutdown on 2009-08-08
anyone ?

---

### Post by lswb on 2009-08-08
I'm not sure if this is what it is for, but while connected, right click on the NetworkManager applet icon, select Edit Connections/Mobile Broadband, click on the entry to highlight your provider, then click "edit". In the dialog that then appears there is a check box for "Connect automatically" Unfortunately the "ppp settings" tab only lists a handful of options, and "persist" or "on demand" are not among them. 

If that doesn't work, it is still possible to set up a ppp connection independant of NM, using say pppconfig/pon/poff and put whatever options you like in the /etc/ppp/peers/provider file for that isp.

---

