---
title: "Hp dm1z/hp mini 210 Compatibility?"
date: 2012-04-25
forum: General Help
---

### Post by davidftechman on 2012-04-25
Has anyone here used or are using one of these netbooks with linux 11.10 or 12.04 and if so does everything work?Im wondering which one to get that has more compatibility and not be stuck with something that doesnt work.The two particulary os that i would use is ubuntu or xubuntu.

---

### Post by ts3 on 2012-04-25
HP dm1z with 12.04 here (ran 11.10 until about a month ago) (this one [http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=QD992UA%23ABA&aoid=20715&ci_src=14110944&ci_sku=QD992UA#ABA](http://www.shopping.hp.com/webapp/shopping/product_detail.do?product_code=QD992UA%23ABA&aoid=20715&ci_src=14110944&ci_sku=QD992UA#ABA))

The only issue I had early on was the specific wireless Broadcom BCM4313 card on 11.10.  The usual drivers work well with most Broadcom cards but not with that particular one so had to do some research to get the wireless to work.  It's not a big issue but can be frustrating for a beginner.  OTOH, I learnt a lot about my system very fast so I'm not complaining :)  It helps to have a wired connection on install.

I made a back-up USB when the laptop first arrived (it doesn't come with any install media) and am mostly single-booting Ubuntu, with other Linux distributions from time to time.  

With 12.04 the wireless and everything else worked pretty much out of the box.

---

### Post by jerrycrabb on 2012-05-02
This is interesting to me. I had the same issues with the wireless prior to 12.04 and am still having issues after the 12.04 install. (fresh installation not an upgrade).

Can I ask what steps you took to fix the wireless before?

---

### Post by techvish81 on 2012-05-02
in all these hp note/netbooks u have to install the bcm driver irrespective of any release (10.04 to 12.04) , which you can easily activate using 'additional hardware drivers ' from the menu/dash . 

in all of these ubuntu  versions u will get the best battery life in 10.04.4 . i dont know but the support may have expired or near to expiry.   in all the versions thereafter  , battery life is very unimpressive . it could be better in xubuntu or lubuntu but it was best in ubuntu 10.04.

---

### Post by ts3 on 2012-05-02
> **jerrycrabb said:**
> Can I ask what steps you took to fix the wireless before?

For 12.04 it was enough to activate the additional drivers in system settings and then run

```
sudo rmmod bcma
sudo rmmod brcmsmac
sudo rmmod wl
sudo modprobe wl
```

to unload and reload the wl driver and remove the conflicting drivers.  I also blacklisted the bcma and brcmsmac drivers in /etc/modprobe.d/blacklist.conf.  I did that early on though, think it was the first beta version.  I understand that for some reason now the additional drivers do not always activate.  Installing bcmwl-kernel source, broadcom-sta-source and broadcom-sta-common from the software centre amounts to the same thing and should work.  

Cheers

P.S.  Now I think about it I probably should not say that the wireless worked out of the box on 12.04, it's just that I found it much easier to fix.  On the other hand, the default brcmsmac driver did give me some wireless connection, albeit very slow, unlike 11.10 when it did not work at all.  I quite look forward to when the default driver works for this particular wireless card.

---

