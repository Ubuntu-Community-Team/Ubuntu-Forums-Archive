---
title: "Browsers very slow in 9.10."
date: 2009-11-02
forum: General Help
---

### Post by old_geekster on 2009-11-02
I did a clean install of 9.10.  It went extremely well.  All of my components were recognized and setup properly.  However, my browsers, Chrome and Firefox, are operating very slowly.  In fact, I could have opened 20 links in 9.04, in the time that it takes to open one link in 9.10.  I am using DSL for my Internet connection.  I don't expect to solve the problem, simply make the problem known.  I expect it to take an update to do the trick.

---

### Post by mitchellcipriano on 2009-11-03
I am having the same issue on two machines I have running 9.10. It seems to be a DNS issue, because the browser seems to hang while looking up the page. This is a new problem for me to 9.10. I did not experience it with 9.04.

---

### Post by Duskao on 2009-11-05
I am also having the same issue with any webkit based browsers I have tried in ubuntu 9.10. I also have a similar issue with opera, but I had this issue with 9.04 as well. I used chromium/chrome, and midori on 9.04 and they were lightning fast. Right now my fastest is the slug FF.

---

### Post by MrTim on 2009-11-06
Same issue here. Taking ages to lookup names. Once it's done this it is usually OK, as long as it doesn't have to lookup any more names. Speed testers show the line is pretty good, once it's resolved the site's name. It's pretty much unusable as it is and I have had resort to using one of my Windows machines for browsing.
 
I also have issues with the Ubuntu startup music, which skips around like a broken record, and it also keeps losing my keyboard and mouse (which it did during the upgrade forcing me to reboot).
 
All in all, not a particularly good experience so far, and I've had to abandon it for now.

---

### Post by EvilBro on 2009-11-06
I had the same problem. I think I 'solved' it by changing the following in the NetworkManager: I right clicked the icon in the 'tray', went to edit connections, selected eth0 and clicked edit, went to the IPV4 tab, changed it to "Automatic (DHCP) addresses only" and added the DNS server my provider uses/provides (router 192.168.1.1 did not work for me). Disconnected and reconnected after applying, and everything went smooth again.

I do have a question though: my provider specifies two dns servers. How can I enter both in the networkmanager?

---

### Post by MrTim on 2009-11-29
If fixed mine (I hope) by disabling ipv6 in Firefox.  Go to about:config, pass the 'Here be dragons' warning, then change the value of network.dns.disableIPv6 to false.

I believe the problem is an incompatibility with my oldish Vigor router, ie it doesn't understand ipv6 very well (or at all).  I'll see if I can get an firmware update for it, but for now the Firefox mod seems to have worked.

---

### Post by Macchi on 2009-12-04
I confirm that I also experienced similar problems of slow browsers on two laptops with 9.10. As a reference all other machines with Mac OS X, Windows, Ubuntu 8.10 and Ubuntu 9.04 on the same network are not subject to the same problem.

PS: Toggling network.dns.disableIPv6 to TRUE did the trick. That is DISABLING IPV6, thus the opposite of MrTim's solution mentioned above.
Regressions? I seem to remember similar problems with IPV6 back in 2004 or 2005 on SuSE & RedHat

---

