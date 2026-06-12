---
title: "Recommendations for recovery - no route to router"
date: 2010-03-24
forum: General Help
---

### Post by buchs on 2010-03-24
Now I've done  it!  I messed up my Karmic install on my laptop trying to get wireless  networking connection to behave better.  I'm not really sure what I did,  but the problem I have is that, though it connects to my wireless  network, it does not get a route to it.  Any attempt to reach the router  with a ping yields a destination unreachable.  Trying to fix it in true  hack fashion, I tried messing around with the static routes.  I added  an explicit route for my router  (route add 192.168.0.1 wlan0) with no  avail.  I ensured there was a default route to the router which is a  gateway outside of my LAN (route add default wlan0 gw 192.168.0.1).  I  have another route to my LAN network with a gateway of "*".  I've done  all this but the results are the same.

So, I'm interested in recommendations to fix this.  Is there some  networking setup/install procedure I can rerun?  Does a recovery boot work?  Or is it best to go  back and reinstall Karmic?  Are there other places that you might  suggest I look to in order to fix this?

Thanks much!

---

### Post by kamaji792 on 2010-03-24
Have you tried the Karmic - Internet and Networks doc page:

[https://help.ubuntu.com/9.10/internet/C/index.html](https://help.ubuntu.com/9.10/internet/C/index.html)

All the best

---

### Post by buchs on 2010-04-16
> **buchs said:**
> Now I've done  it!  I messed up my Karmic install on my laptop trying to get wireless  networking connection...

My resolution (not solution) was to stop using a static IP connection.  See: [http://ubuntuforums.org/showthread.php?p=9130309#post9130309](http://ubuntuforums.org/showthread.php?p=9130309#post9130309)

---

