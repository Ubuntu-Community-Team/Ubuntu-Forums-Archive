---
title: "How to disable a wireless card"
date: 2011-12-08
forum: General Help
---

### Post by spec36 on 2011-12-08
I have two wireless cards. wlan0 is built into the laptop and wlan1 is a usb wifi stick. Wlan0 is dead, but keeps interfering with my wlan1 on connection attempts. I have to manually select wlan1 every time I connect. how can I disable wlan0 so it never connects again?

Thanks

---

### Post by pastalavista on 2011-12-08
Please post the output from terminal of these commands```
sudo lshw -C network
sudo lsmod
```

---

