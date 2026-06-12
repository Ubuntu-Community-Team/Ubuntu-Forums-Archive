---
title: "ip address of my remote computer"
date: 2011-07-09
forum: General Help
---

### Post by adityavpratap on 2011-07-09
Hi,

I want to transfer files from my laptop to my desktop remotely over the net. Both these computers access net via different service providers and have dynamically assigned IP addresses. If I know the IP address, I can use ssh to accomplish my task. However if I don't have physical access to the desktop, I cannot know the IP address. 

Is there a way by which a the desktop sends its public IP address to me so that I can establish ssh connection ?

---

### Post by spiky001 on 2011-07-09
As far as I know that is how it is You need the ip address. An option for later would be a dyns [http://www.dyndns.com/](http://www.dyndns.com/)

---

### Post by MrEgg on 2011-07-09
+1 on what Spiky001 said.

On DynDNS, you must at least register the remote machine you want to connect to. You can register both machines if you want to be able to contact either one of them.

You can update your dynamic ips either through your routers (most support this feature), or right from your 2 ubuntu systems using ddclient (sudo apt-get install ddclient).

---

