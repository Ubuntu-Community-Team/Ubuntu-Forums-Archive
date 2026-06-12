---
title: "WLAN works, but it doesn't work."
date: 2006-04-01
forum: General Help
---

### Post by wlankatt on 2006-04-01
I tried to install my D-Link DWL-122 on Ubuntu. In network settings it says: "The interface WLAN is active" under Wireless Connections, but the internet won't work. What's wrong?

Ifconfig says this:
[http://i73.photobucket.com/albums/i220/snowthorn-artanis/uh.jpg]("http://i73.photobucket.com/albums/i220/snowthorn-artanis/uh.jpg")

Network settings says this:
[http://i73.photobucket.com/albums/i220/snowthorn-artanis/Untitled.jpg]("http://i73.photobucket.com/albums/i220/snowthorn-artanis/Untitled.jpg")

I hope someone can help, if not i have to change to windows. :C

---

### Post by wlankatt on 2006-04-01
Please help! ](*,)

---

### Post by Ramses de Norre on 2006-04-01
Do you need eth0? Otherwise disable it, that solved the same issue for me.
Click on properties and uncheck "enable this connection".

---

### Post by wlankatt on 2006-04-01
I've tried both with and without eth0, but nothing works. :/

---

### Post by Ramses de Norre on 2006-04-01
What exactely does firefox say?
What's the output of ping -c 3 [www.ubuntuforums.org](www.ubuntuforums.org) and ping -c 3 82.211.81.186 ?

---

### Post by jamesr on 2006-04-01
Can you ping the router or adsl modem?

post the output of```
cat /etc/resolv.conf
```

---

