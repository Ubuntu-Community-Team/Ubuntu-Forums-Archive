---
title: "Download Chrome"
date: 2010-09-06
forum: General Help
---

### Post by jimmynCR on 2010-09-06
Is it ok to download Google Chrome now, if so, what is the best way.

---

### Post by OpressedCalamity on 2010-09-06
> **jimmynCR said:**
> Is it ok to download Google Chrome now, if so, what is the best way.

Hello, click this link to download the Google Chrome browser.
[http://www.google.com/chrome/eula.html?brand=CHMB&utm_campaign=en&utm_source=en-ha-na-us-sk&utm_medium=ha&installdataindex=homepagepromo](http://www.google.com/chrome/eula.html?brand=CHMB&utm_campaign=en&utm_source=en-ha-na-us-sk&utm_medium=ha&installdataindex=homepagepromo)
Choose your distro and architecture 32 bit/64 bit, if your not sure which one choose 32 bit
when its done downloading its as simple as double clicking it

---

### Post by Chesamo on 2010-09-06
I'm not sure what you mean by "OK to download Google Chrome" since it's been available for Linux for quite some time.

It's simple to install Chrome (or rather, Chromium... the upstream version). Just open up Terminal and run the command: ```
sudo add-apt-repository ppa:chromium-daily
``` then ```
sudo apt-get update
``` then ```
sudo apt-get install chromium-browser
``` There's a version of chromium-browser in the default Ubuntu repositories, but it's a little behind the daily PPA.

The advantage to installing Chromium from the repositories is that you get automatic updates from the Chromium PPA... I've heard that the Chrome .deb file adds the Google repositories but I'm not on Linux at the moment so I can't test it.

---

### Post by jimmynCR on 2010-09-07
I ran this command and ended up with   E: Couldn't find package chomium-browser

---

### Post by crichard on 2010-09-07
PPAs for Chromium could be found here:
[https://launchpad.net/chromium-project]("https://launchpad.net/chromium-project")

I prefer to install PPA for Ubuntu [Chromium - Dev Channel]("https://launchpad.net/~chromium-daily/+archive/dev") because daily updates are quite annoying me. 
Follow the commands below to add Chromium - Dev PPA & install Chromium
```
sudo add-apt-repository ppa:chromium-daily/dev
``` 
```
sudo apt-get update
``` 
```
sudo apt-get install chromium-browser
```

---

