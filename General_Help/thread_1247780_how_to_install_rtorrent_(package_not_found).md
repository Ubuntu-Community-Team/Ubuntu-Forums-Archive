---
title: "how to install rtorrent? (package not found)"
date: 2009-08-23
forum: General Help
---

### Post by antdgar on 2009-08-23
```
sudo apt-get install build-essential libsigc++-2.0-dev pkg-config comerr-dev libcurl3-openssl-dev libidn11-dev libkadm55 libkrb5-dev libssl-dev zlib1g-dev libncurses5 libncurses5-dev
```

```
Package libcurl3-openssl-dev is a virtual package provided by:
  libcurl4-openssl-dev 7.18.0-1ubuntu2.2
You should explicitly select one to install.
E: Package libcurl3-openssl-dev has no installation candidate

```

Any idea how to solve this?

---

### Post by scouser73 on 2009-08-23
Please follow the instructions set out on this tutorial: [[COLOR="Red"]**UbuntuGeek: How To Install Rtorrent**[/COLOR]]("http://www.ubuntugeek.com/how-to-install-the-latest-rtorrent-and-libtorrent.html")

---

### Post by antdgar on 2009-08-23
I did follow that tutorial. And I got this error:

> Package libcurl3-openssl-dev is a virtual package provided by:
  libcurl4-openssl-dev 7.18.0-1ubuntu2.2
You should explicitly select one to install.
E: Package libcurl3-openssl-dev has no installation candidate

---

### Post by oldos2er on 2009-08-23
Check System, Administration, Software Sources, and make sure all repositories are enabled.

---

