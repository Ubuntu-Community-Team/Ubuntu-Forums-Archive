---
title: "Integrating Thunderbird into messaging indicator in Natty"
date: 2011-05-21
forum: General Help
---

### Post by Kruger2147 on 2011-05-21
I use Thunderbird for my email, and I cant figure out how to integrate it into the message indicator. I downloaded an .xpi file and tried installing it, it would work. I've done some other research and only found stuff for older versions of ubuntu, but nothing for integrating it in Natty

---

### Post by Rasa1111 on 2011-05-21
Got it integrated into my 11.04..
[ATTACH]192836[/ATTACH]

use these instructions..
[http://www.webupd8.org/2011/02/thunderbird-indicator-adds-folders.html](http://www.webupd8.org/2011/02/thunderbird-indicator-adds-folders.html)
```
sudo add-apt-repository ppa:ruben-verweij/thunderbird-indicator
``````
sudo apt-get update
``````
sudo apt-get install xul-ext-indicator libnotify-bin
```

There's also a .deb package for 11.04.
(same one linked at webupd8 link)
[https://launchpad.net/~ruben-verweij/+archive/thunderbird-indicator/+files/xul-ext-indicator_1.4-0ubuntu1_all.deb](https://launchpad.net/~ruben-verweij/+archive/thunderbird-indicator/+files/xul-ext-indicator_1.4-0ubuntu1_all.deb)

and this might be useful to..
[http://www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/](http://www.techgarten.com/ubuntu/replace-evolution-thunderbird-completely-ubuntu/)

---

### Post by Kruger2147 on 2011-05-21
Perfect, thank you.

---

### Post by Rasa1111 on 2011-05-23
:) Most welcome.

---

