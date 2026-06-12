---
title: "Missing network manager icon"
date: 2011-01-17
forum: General Help
---

### Post by begroup on 2011-01-17
Hello
I installed ubuntu10.04 on my Copaq laptop. I configured net on it.
After some days, thte network manager icon in the panel suddenly disappered. 
Could anybody tell me how to recover network manager applet icon??
Thank u  in advance !

---

### Post by RedSingularity on 2011-01-17
Right click the panel and select "add to panel".  Add the "notification area" to the panel.  See if your icon is back after that.

---

### Post by begroup on 2011-01-17
Thank you for the reply.
I tried doing that, but still the icon is not appearing. 
Also on pinging, it says "network unreachable".
Any help ??

---

### Post by RedSingularity on 2011-01-17
So you dont have Internet on that machine now?

---

### Post by begroup on 2011-01-17
Yes there is Internet on the laptop.
After adding the eth0 entry through interfaces, net started.
But still the icon is missing.
I tried tracing why it disappeared. I guess it disappeared bcoz I removed libpcap-0.8 package from my laptop. Is this really the reason ?

---

### Post by Script Warlock on 2011-01-17
you can try to reset the panel if you want to..

---

### Post by begroup on 2011-01-17
I tried adding the notificaton area to the panel. But still no change !
I configured the net on the laptop manually.
Now i try to run "apt-get update"command. It gives error as : "No address associated with hostname"
any help ??

---

### Post by RedSingularity on 2011-01-17
What happens when you run:

nm-connection-editor

---

