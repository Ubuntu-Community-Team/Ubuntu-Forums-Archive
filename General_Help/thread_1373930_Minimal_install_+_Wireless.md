---
title: "Minimal install + Wireless"
date: 2010-01-06
forum: General Help
---

### Post by pedrom169 on 2010-01-06
When I have completed the cli install. Am I able to connect to the wireless to start downloading packages?

If so are there any guides I can read through to find out?

Thank you

---

### Post by nothingspecial on 2010-01-06
```
sudo ifconfig wlan0 up

sudo iwconfig wlan0 essid networkname_here


sudo iwconfig wlan0 key passphrase_here

sudo dhclient

sudo apt-get update && sudo apt-get upgrade
```

---

