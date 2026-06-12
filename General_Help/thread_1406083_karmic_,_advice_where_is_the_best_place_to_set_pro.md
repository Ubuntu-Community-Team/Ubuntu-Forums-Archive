---
title: "karmic , advice where is the best place to set proxy"
date: 2010-02-13
forum: General Help
---

### Post by graemev on 2010-02-13
1: OK I have a number of machines sitting behind a proxy.
2: there is that tempting application on the menu which launches gnome-network-preferences
3: It allows me to click the button 'apply-system-wide'  ... but it not clear what that does?
4: in my environment I end up with http_proxy=http://xx.xx.xx.xxx:yyyy/ where xxx & yyyy are reasonable numbers ... but still that horrible trailing slash (which breaks googleearth & many other apps) 

5: I've noticed that things such as popularity-contest always fail  ... so I wondered if http_proxy is getting set early enough that cron jobs (not MY children of course) get the right environment.
(if I run the cron job from a root shell it works fine)

6: I'm tempted to add it to /etc/environment and simply remove the GUI setting

Any words of advice? ... failing that what 'component' is gnome-network-preferences ?

---

