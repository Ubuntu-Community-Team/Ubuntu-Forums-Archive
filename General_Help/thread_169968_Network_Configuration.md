---
title: "Network Configuration"
date: 2006-05-03
forum: General Help
---

### Post by zBoost on 2006-05-03
Ok, today I installed Ubuntu 5.10 on my server so I have 2 pc's one with Windows XP and the server with Ubuntu 5.10. So I installed it with server parameter. Now both pc's are lan connected buth while i was installing ubuntu, they weren't connected and choose to setup the network later. From windows it displays the network connected, but i have to setup the network from linux, ifconfig eth0 shows only the mac adress and nothing more. How I can setup the network from terminal, IP's, gateway etc, can it be auto detected ?

---

### Post by nanotube on 2006-05-03
try
```
sudo ifup eth0
```

---

