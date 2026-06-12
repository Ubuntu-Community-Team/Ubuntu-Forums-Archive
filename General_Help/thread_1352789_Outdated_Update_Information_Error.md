---
title: "Outdated Update Information Error"
date: 2009-12-12
forum: General Help
---

### Post by Radiofloyd on 2009-12-12
When I select the outdated triangle on Ubuntu Koala and checks for updates it shows this error after checking 51 updates...

"Failed to fetch [http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/Release](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu/dists/karmic/Release)  Unable to find expected entry  mai/source/Sources in Meta-index file (malformed Release file?)

Some index files failed to download, they have been ignored, or old ones used instead."

I have been able to update with the auto updates Ubuntu has loaded, but I feel my machine is not fully upgraded.  Does anyone know what this means?  I am fairly new to Ubuntu, been using since 8.10 but for casual operations.

Any help is much appreciated.  Thank you.

---

### Post by aot2002 on 2009-12-12
remove that package and get the chrome from linux version since it's out now

sudo gedit /etc/apt/sources.list
remove the ppa line

sudo apt-get update


install from here below

[http://www.google.com/chrome?platform=linux&hl=en](http://www.google.com/chrome?platform=linux&hl=en)

---

### Post by Radiofloyd on 2009-12-12
Thank you!  I will do this when I get home later, thanks again.

---

