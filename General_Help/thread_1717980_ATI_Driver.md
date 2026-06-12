---
title: "ATI Driver"
date: 2011-03-30
forum: General Help
---

### Post by &#1103;&#1091;&#1076;&#1080; on 2011-03-30
Whenever I play minecraft of my Linux computer it lags like mad. Someone over on the minecraft forums told me to make sure I had the right video drivers.

I know I have an ATI FireGL V3100 video card but I don't know how to update the driver.

Help?

EDIT: Idk if this matters but I am running Ubuntu 10.10

---

### Post by &#1103;&#1091;&#1076;&#1080; on 2011-03-30
Ok nvm I found the driver. But it downloaded as a .zip file. How do I install it

---

### Post by Krytarik on 2011-03-30
Did you install any driver so far?
Maybe via "System -> Administration -> Additional Drivers"?

Please post the ouputs of the following commands:
```
lshw -c video
dpkg -l |grep fglrx
```You shouldn't install the driver manually with the mentioned installer, because
- it is not a safe install, you can't remove the driver easily and safely
- you have to re-install the driver each time when the kernel gets upgraded
- the driver will not get updated automatically
- the driver is not necessarily considerably more recent
- the driver doesn't necessarily provide a considerable higher performance

---

### Post by Mark Phelps on 2011-03-31
Looks like you may have made a bad choice regarding gaming and your video card.  See the link below:

[http://news.tigerdirect.com/2008/05/14/ati-firegl-v3100-video-card/]("http://news.tigerdirect.com/2008/05/14/ati-firegl-v3100-video-card/")

---

