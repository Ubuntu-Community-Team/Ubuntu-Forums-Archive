---
title: "Trouble with wireless connections"
date: 2012-03-14
forum: General Help
---

### Post by Sanada1615 on 2012-03-14
Hello, I am running Ubuntu 11.10/Windows 7 on a Toshiba Laptop. Windows came preloaded, as usual. Since dual-installation, Ubuntu has had a few nagging problems. The major one is that the only time I can get it to connect to wireless networks properly is upon a fresh boot or reboot. If I put 'er to sleep, and then power back up, it can find the network, and shows activity in the wireless icon, but it never fully connects, ever. Windows has no problems with wireless at all. Any suggestions? It's annoying having to reboot just to use wireless, and it's slowing my conversion to dedicated Linux-user.

---

### Post by MSPdwalt on 2012-03-14
Please post the output of:

```
sudo lshw -C Network
```

This will tell us what kind of wireless card you have/what card Ubuntu thinks you have.

---

