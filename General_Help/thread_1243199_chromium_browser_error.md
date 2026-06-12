---
title: "chromium browser error"
date: 2009-08-18
forum: General Help
---

### Post by oboedad55 on 2009-08-18
Hi, when I try install Chromium browser I get this error. I'm doing it from a terminal because it doesn't show up in synaptic. I edited sources.list from root since I can't save it as user. Is this a permissions problem?

apt-get install chromium-browser

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by Soul-Sing on 2009-08-18
try: ```
sudo apt-get install chromium-browser
```
You should add the chromium  PPA to your sources.list: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
how to: [http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html](http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html)
or: [http://www.psychocats.net/ubuntucat/chromium/](http://www.psychocats.net/ubuntucat/chromium/)

---

### Post by oboedad55 on 2009-08-18
> **leoquant said:**
> try: ```
sudo apt-get install chromium-browser
```
You should add the chromium  PPA to your sources.list: [https://launchpad.net/~chromium-daily/+archive/ppa](https://launchpad.net/~chromium-daily/+archive/ppa)
how to: [http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html](http://www.ubuntugeek.com/how-to-install-chromium-google-chrome-in-ubuntu-using-deb-package.html)
or: [http://www.psychocats.net/ubuntucat/chromium/](http://www.psychocats.net/ubuntucat/chromium/)

Geez, it's getting late. sudo, now there's a thought! Thanks for the reminder.

Jon

---

### Post by MichealH on 2009-08-18
And you could save the file as user if you had went to the directory and typed
```
sudo chmod 777 sources.list
```
and saved It ;)

---

### Post by oboedad55 on 2009-08-18
> **MichealH said:**
> And you could save the file as user if you had went to the directory and typed
```
sudo chmod 777 sources.list
```
and saved It ;)

Is that something that should be set that way? Both of my systems have sources.list set as root. I remembered I can do, gksudo. That way I can save the sources.list.

Thanks,
Jon

---

