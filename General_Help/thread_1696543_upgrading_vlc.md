---
title: "upgrading vlc"
date: 2011-02-27
forum: General Help
---

### Post by sainath90 on 2011-02-27
currently im using vlc 1.1.4..how can i upgrade it to 1.1.7 which is the latest release

---

### Post by flipper T on 2011-02-27
Open the terminal and run the following commands

sudo add-apt-repository ppa:n-muench/vlc

sudo apt-get update

sudo apt-get install vlc mozilla-plugin-vlc

---

### Post by Krytarik on 2011-02-27
Since you already have VLC installed, you just have to "upgrade" after adding the PPA, "install" won't work:
```
sudo add-apt-repository ppa:n-muench/vlc
sudo apt-get update
sudo apt-get upgrade
```But I would try to upgrade by using another PPA, this one has fewer implications (regardless of the title it works only for Maverick by now):
[http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html](http://www.webupd8.org/2010/08/install-vlc-114-in-ubuntu-via-new-ppa.html)

PS: Lucid users can use this PPA, officially recommended by VLC's devs:
[https://launchpad.net/~lucid-bleed/+archive/ppa]("https://launchpad.net/%7Elucid-bleed/+archive/ppa")

---

