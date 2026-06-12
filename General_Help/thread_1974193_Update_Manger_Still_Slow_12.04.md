---
title: "Update Manger Still Slow 12.04?"
date: 2012-05-05
forum: General Help
---

### Post by TurtleKing on 2012-05-05
Am I the only one experiencing this problem? Every time I check for updates, it takes 5-10 minutes for it to finish. I had thought it was because of the 12.04 download demands, but a week has past and it's still just as slow (even in Kubuntu).

---

### Post by tomatoe on 2012-05-05
Works fast for me...

---

### Post by wilee-nilee on 2012-05-05
I use apt-fast, here are two links one for a description and one for a debi for easy install. This may not be the latest script that can be manually installed, but works fine and with a deb, a easy install.

[http://www.addictivetips.com/ubuntu-linux-tips/accelerate-apt-get-downloads-in-ubuntu-with-apt-fast/](http://www.addictivetips.com/ubuntu-linux-tips/accelerate-apt-get-downloads-in-ubuntu-with-apt-fast/)

[http://www.mattparnell.com/linux/apt-fast/henrique/](http://www.mattparnell.com/linux/apt-fast/henrique/)

---

### Post by dcstar on 2012-05-05
> **TurtleKing said:**
> Am I the only one experiencing this problem? Every time I check for updates, it takes 5-10 minutes for it to finish. I had thought it was because of the 12.04 download demands, but a week has past and it's still just as slow (even in Kubuntu).

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/977906](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/977906)

---

### Post by TurtleKing on 2012-05-07
> **dcstar said:**
> [https://bugs.launchpad.net/ubuntu/+source/apt/+bug/977906](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/977906)

Is there a fix for it, yet? (or does canonical know about it at least?)

By the way, I live in Pennsylvania, USA (in case I was suppose to change something in default).

---

### Post by fragos on 2012-05-07
You can find the fastest mirror by opening Update Manager and click the Setting... button. Now select the Ubuntu Software tab. Click the drop down menu for Download from... Select Other and a window will pop up choosing a download server. Click the Select Best Server button and wait for the search to complete. PPA's you've added may not be sourced from these Ubuntu mirror servers. Those may be slower. I've noticed that the Google PPA's can be slow at times. I changed from Chrome to Chromium which is served by Ubuntu and removed the Google PPA -- it's always fast now.

---

