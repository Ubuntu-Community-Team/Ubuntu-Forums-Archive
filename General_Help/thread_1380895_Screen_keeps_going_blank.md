---
title: "Screen keeps going blank"
date: 2010-01-14
forum: General Help
---

### Post by alanrlow on 2010-01-14
Since a recent kernel upgrade when left untouched for 10 minuets my Acer Aspire 3500 running Ultimate edition Ubuntu screen goes blank. I can just sort of see it blinking with the backlight off and if I touch the pad or a key it pops back no worries. If however I leave it for a half hour or so nothing will wake it up and my only option is a hard reset via the power button, even tho things are still running. For example I can be playing an MP3 and I can come back later and the screen is blank, still playing but I'm stuck and can't do anything except hit reset.  Help.

Alan

---

### Post by scouser73 on 2010-01-14
It sounds as if you may need a program called Caffeine.

[[COLOR="Red"]**Launchpad PPA for Caffeine**[/COLOR]]("https://launchpad.net/~caffeine-developers/+archive/ppa")

**1** - Click [B]Technical Details about this PPA
[/B]
**2** - Click on the **Choose your Ubuntu version** drop-down menu

**3** - Go to **Administration** > **Software Sources**

**4** - Enter your password

**5** - Click the **Other Software** tab

**6** - Click **Add**


[COLOR="Red"]**If you are using Ubuntu 9.04, then copy the following two lines**[/COLOR]

**7** - > **deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) jaunty main**

**8** - > **deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) jaunty main**

[COLOR="Red"]**If you are using Ubuntu 9.10, then copy the following two lines**[/COLOR]

> **deb [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) karmic main**

> **deb-src [http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu](http://ppa.launchpad.net/caffeine-developers/ppa/ubuntu) karmic main**

**9** - Click **Close**, then click **Reload**

**10** - Open Terminal, copy & paste this command 
> **sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 569113AE**

**11** - Copy & paste this command > **sudo apt-get update**

**12** - Go to Administration > Synaptic Package Manager and enter **caffeine** in the search field & right click **Mark For Installation**

**13** - Click **Apply** & then click **Apply** again

Caffiene will now be installed & will be in the **Accessories** menu

---

