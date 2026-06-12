---
title: "Ubuntu Just works, Laptop and Wireless"
date: 2006-03-10
forum: General Help
---

### Post by berlinbrown on 2006-03-10
I was reading up on wireless cards and laptops and just getting myself ready for when it wouldn't work.  Guess what, it just worked.  I was really shocked.  I didn't have to touch a config file or anything.  Also, I didn't need to touch ebay for some rare pcmcia card either.

For those who want the hardware information.  I have a Thinkpad Laptop, 800mhz, 512MB ram, 20gig, DVD.

I have a Belkin Network card (Actually, I the default ethernet card didnt work, no biggie).  I also have a Belkin Wireless Card:

Belkin High-Speed 802.11g Wireless-G Notebook Card
Model: F5D7010

Like, I mentioned before.  I am not into fancy, so I normally buy stuff and BestBuy.  The belkin wireless card was 34.99 (I believe).

Actually, I did go ahead and apt-get wifi-radar.  Also, I needed to run through the Networking settings a coupld of times to enable ath0.  After that, I ran 'dhclient ath0'.  Note, I don't know if this is worthy or not, but just dhclient, didnt seemed to work, I needed to specify the device.

<p>
Ubuntu Just Work, Berlin Brown
<p>
[http://www.newspiritcompany.com]("http://www.newspiritcompany.com")

---

### Post by eltaito on 2006-03-10
glad to hear everything works for you.......Ubuntu did a great job of hardware detection and setup on my laptop as well (emachines 5310 running Breezy) with the exception of the pesky built in wireless card which has the dreaded Broadcom chipset (definately not Ubuntu's fault...can blame broadcom for that one).....but all in all, Ubuntu is the best distro I have tried in terms of hardware detection, stability, and community help......hope they keep up the great work.

---

### Post by steel_j on 2006-03-10
Same for me with my HP Omnibook XE3 GC and my PCMCIA US Robotics wifi card..Every other distro I had to fiddle with config files and install ACX100 drivers by hand...Now it just installed it and it works plug and play...

---

### Post by ESM on 2006-03-10
The daily Dapper release has problems with wireless in any case. 5.10 detected my system without any problems but in Dapper they have now done something strange: a second detection in the panel and that one doesn't detect anything. Yep, it detects the cards, but that's it. And thus the internet doesn't work at all.

---

### Post by eltaito on 2006-03-11
yeah I tried Dapper out on a partition a few weeks ago...it worked out pretty good for me....but only because I long ago tired of fiddling with ndiswrapper and my broadcom card so I "bit the bullet" and bought a $30 PCMCIA card (Netgear 511T) that works great in Breezy and Dapper (as long as you have restriced modules with Madwifi installed).  But I have heard of some wireless issues in Dapper...but we are still about a month away from the Full release with rumors of a 6 week delay to fix some issues.....so hopefully they'll iron that out....they've done a great job of that so far.

---

### Post by closeyourwindows on 2006-03-11
I went through some issues when I first installed the wireless but that was just lack of experience in linux.  I have wpc54g broadcom card and have no problems.  I love it and it does just work.  Since then I have re installed and have had no issues and it is a snap

---

