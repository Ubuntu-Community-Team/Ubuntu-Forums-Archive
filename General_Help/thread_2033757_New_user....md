---
title: "New user..."
date: 2012-07-26
forum: General Help
---

### Post by Kdmjr94 on 2012-07-26
I'm a brand new user to Lubuntu and I have Lubuntu 12.04 I believe and I cannot find a way to install the drivers for my DYNEX Wireless Enhanced G. It's the one that is on this page:
[http://www.zimbio.com/Laptop+Reviews/articles/5e8gJ3Cy4Sq/Dynex+DX+EBUSB+125Mbps+802+11g+Wireless+LAN](http://www.zimbio.com/Laptop+Reviews/articles/5e8gJ3Cy4Sq/Dynex+DX+EBUSB+125Mbps+802+11g+Wireless+LAN)

And I cannot seem to get it to run on my Lubuntu, and since I'm a new user, I have no clue on how to work it. Lol. I would love to get it to work on my Lubuntu, since it already works on my Windows 7 and I want a new OS, so I went with Lubuntu. Please help me, and thank you in advance. :)

---

### Post by Cheesehead on 2012-07-26
Other questioners with the same issue ( example: [https://answers.launchpad.net/ubuntu-vancouver-loco-tech-support/+question/159413](https://answers.launchpad.net/ubuntu-vancouver-loco-tech-support/+question/159413) ) seems to indicate that hardware has a Broadcom 4318 chipset.

If so, the the following command will automatically download and install the correct kernel module (driver) for your otherwise incompatible hardware. While connected to the internet, open a terminal window and enter:```
sudo apt-get install firmware-b43-installer
```

After the package manager has installed, you will need to reboot for the new kernel module to load properly. (There are ways to load the module without rebooting, but rebooting is the simplest).

If your hardware works afterward, please use the Thread Tools on this page to make the thread [SOLVED].

If your hardware still does not work afterward, take a look at the help page specifically for that family of Broadcom chipsets: [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

