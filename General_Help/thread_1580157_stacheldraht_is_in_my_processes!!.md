---
title: "stacheldraht is in my processes!!"
date: 2010-09-22
forum: General Help
---

### Post by drink_stir on 2010-09-22
i have found stacheldraht is running in one of my active connections. i did some reading and found that this is not a good thing. not a good thing atall!!! i dont know if someone installed a rat on my system or what but the activity on the sent side was going crazy when it was running. 

Does anyone know what I am dealing with? and if so how to fix it?

---

### Post by CharlesA on 2010-09-22
Was it listened in netstat?

---

### Post by drink_stir on 2010-09-22
I didnt check netstat. i was looking in my active connections in firestarter and when i seen how much was being sent i tried to lock my firewall and it gave me some "unknown error" and wouldnt lock so i restarted and its not there anymore. the only connections i have now are my pidgin, firefox and an unknown through port 61843. i cant find anything on that port through google. not sure if its connected to the stacheldraht thing. but i just did a netstat -l and there are alot of listening servers. most of which are netbios-ns and netbios-dgm. i dont see the ip from the stacheldraht  among them but alot of the ips are *'d out. im kinda lost here.

---

### Post by CharlesA on 2010-09-22
You are fine.

Firestarter is no longer in development, and it's better to use something like gufw or ufw.

---

### Post by drink_stir on 2010-09-22
i have been having ddos type problems. i think anyway... when my firewall is running some sites wont load. so i put an exception in the firewall and they still dont run. but when i drop my firewall they run just fine. im just not sure whats going on. and this kinda freaked me out.

---

### Post by CharlesA on 2010-09-23
Blame firestarter. Use something like GUFW or the like.

---

### Post by drink_stir on 2010-09-23
i have gufw on my computer but thought firestart was the better one. i found this particular problem only shows up when i am downloading torrents. i just blocked the port and no more problem.

Thanks.

---

