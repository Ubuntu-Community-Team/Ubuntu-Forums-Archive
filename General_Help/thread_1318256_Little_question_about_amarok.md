---
title: "Little question about amarok"
date: 2009-11-07
forum: General Help
---

### Post by lithmariel on 2009-11-07
How to install old version? I upgraded my ubuntu and got that ugly, shitty looking 2.2 amarok, I want my old version back T.T

And I think this is no place for it, but there should be a option to let us check what we didn't want to install while getting a newer version of ubuntu....

Edit: Solved with this:

sudo gedit /etc/apt/sources.list

Add lines:

deb [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main
deb-src [http://ppa.launchpad.net/bogdanb/ppa/ubuntu](http://ppa.launchpad.net/bogdanb/ppa/ubuntu) jaunty main

Then just install

sudo apt-get update
sudo apt-get install amarok14

Yay!

---

