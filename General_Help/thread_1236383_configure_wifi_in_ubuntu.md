---
title: "configure wifi in ubuntu"
date: 2009-08-10
forum: General Help
---

### Post by nipunreddevil on 2009-08-10
How do i configure wi fi in ubuntu 9.04.I know all my addresses and am able to easily connect in windows using these.i.e.i know my ipv4 settings

---

### Post by 3rdalbum on 2009-08-10
> **nipunreddevil said:**
> How do i configure wi fi in ubuntu 9.04.I know all my addresses and am able to easily connect in windows using these.i.e.i know my ipv4 settings

Well, it's odd that you'd need all that on Windows, but it's easy to configure your wifi.

Near the top-right corner of the screen, on the top panel, you'll see an icon that looks like two little computers; or you might see an icon that's four empty grey signal bars. Click on that, and then click on your wireless network's SSID. You'll be prompted to type in your password or key, and then you will connect to the network.

That is, if your wireless card is supported out-of-the-box on Ubuntu. Most are. If it isn't and you don't see any wireless networks when you click on the Network Manager, then you will need to give us the output of these commands:

```
lspci
lsusb
```

so we know what wireless card you have, and can advise you of what driver you need to install.

---

### Post by nipunreddevil on 2009-08-12
I am getting wi fi signal but am not able to connect to them in ubuntu?

---

