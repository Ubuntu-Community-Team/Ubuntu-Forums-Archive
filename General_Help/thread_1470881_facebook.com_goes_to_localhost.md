---
title: "facebook.com goes to localhost?"
date: 2010-05-03
forum: General Help
---

### Post by jbeiter on 2010-05-03
ok I haven't seen this before. I just set my sister up on ubuntu 10.4 to rescue her from windows virus hell. She doesn't do much but loves facebook.

Everything installed well and I can get to common sites on firefox like google.com, slashdot, etc...  When I go to facebook.com, [www.facebook.com](www.facebook.com), [http://facebook.com](http://facebook.com), firefox goes to localhost and fails.

dhcp sets up networking from her provider and nslookup returns several IPs for facebook.com. Other sites resolve fine too. I can put the IP for facebook.com in the browser and it works. When she tries to authenticate, it fails again though.

Has anyone see this kind of weirdness before??

---

### Post by burton247 on 2010-05-03
Only seen that kind of stuff in windows when a virus overwrote my hosts file lol. Check /etc/hosts and see if facebook is being sent somewhere else

---

