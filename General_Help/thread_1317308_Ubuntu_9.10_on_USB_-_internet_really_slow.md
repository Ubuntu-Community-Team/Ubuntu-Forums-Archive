---
title: "Ubuntu 9.10 on USB - internet really slow"
date: 2009-11-06
forum: General Help
---

### Post by Callum MacLellan on 2009-11-06
I've just managed to get ubuntu 9.10 running from a pen drive but I've been struck by how slow web pages are to load. Other applications seem to be OK - open office, etc. 

Any suggestions?

---

### Post by bwdease on 2009-11-11
Ok! I just updated to ubuntu 9.10 to find my internet connection was real slow as well.  I searched around and I think I may have stumbled across something here. I found this on another sight, so here goes....
-open firefox
-type "about:config" in the address bar
-click "I'll be careful. I promise."
-in the filter bar type "network.dns.disableIPv6"
-make it "true"
-close firefox and try again.

I noticed a difference right away in my browser. Worth a try for others who are experiencing the same problems. After this change to firefox, It's now normal speed for me. Hope this helps.  Good luck!!!

---

### Post by Minsky on 2009-11-11
> **bwdease said:**
> Ok! I just updated to ubuntu 9.10 to find my internet connection was real slow as well.  I searched around and I think I may have stumbled across something here. I found this on another sight, so here goes....
-open firefox
-type "about:config" in the address bar
-click "I'll be careful. I promise."
-in the filter bar type "network.dns.disableIPv6"
-make it "true"
-close firefox and try again.

I noticed a difference right away in my browser. Worth a try for others who are experiencing the same problems. After this change to firefox, It's now normal speed for me. Hope this helps.  Good luck!!!

The above solution worked for me as well. However, After just installing the latest updates for Firefox, I found the problem resolved for me.

---

### Post by Ragavan Venk on 2009-12-25
Worked for me as well. Thank you!

---

### Post by MeTylerDurden on 2009-12-26
how do you change the value to true when you get to network.dns.disableIPv6

---

### Post by trelozakinthinos on 2010-11-14
Just right click and toggle!
It should turn into true. Hope i helped!

---

