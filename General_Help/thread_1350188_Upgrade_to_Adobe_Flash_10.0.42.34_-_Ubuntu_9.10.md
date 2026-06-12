---
title: "Upgrade to Adobe Flash 10.0.42.34 - Ubuntu 9.10"
date: 2009-12-09
forum: General Help
---

### Post by Terrycymru on 2009-12-09
I have just downloaded the .deb for flash 10.0.42.34 from Adobe. Before attempting to install it I tried to use Synaptic to remove the old version but it failed with an error message:

E: adobe-flashplugin: subprocess installed pre-removal script returned error exit status 2

Anyone else seen this?

---

### Post by Terrycymru on 2009-12-09
I found several suggested solutions on this bug report:

[https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/412944](https://bugs.launchpad.net/ubuntu/+source/adobe-flashplugin/+bug/412944)

I used the suggestion in #6  :

I edited the /var/lib/dpkg/info/adobe-flashplugin.prerm file and commented out the line:

VARIANTS="iceape iceweasel mozilla firefox xulrunner midbrowser xulrunner-addons"

---

