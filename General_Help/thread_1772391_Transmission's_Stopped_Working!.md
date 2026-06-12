---
title: "Transmission's Stopped Working!"
date: 2011-05-31
forum: General Help
---

### Post by chome4 on 2011-05-31
Giving me the message: Requested download is not authorized for use with this tracker. - idle'

Vuze, when I start it, just closes before it even makes itself known!

Can someone let me know of reliable torrent client with multi-tracker support, either deb install or easy to follow terminal instructions?

Thanks.

---

### Post by seawolf167 on 2011-05-31
> **chome4 said:**
> Giving me the message: Requested download is not authorized for use with this tracker. - idle'

This message means that you are attempting to connect to a torrent being tracker by a private tracker which requires an account. Ensure that you have permission to download the torrent (check your ratio, account standing, permissions, etc.).

I have had no problems with Transmission, another good torrent program is Deluge.

It is either

```
sudo apt-get install deluge-torrent
```or

```
sudo apt-get install deluge
```I cannot remember

---

### Post by chome4 on 2011-05-31
When trying to install deluge, I get:

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libboost-python1.37.0 1.37.0-3ubuntu3
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libboost-system1.37.0 1.37.0-3ubuntu3
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libboost-filesystem1.37.0 1.37.0-3ubuntu3
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libboost-thread1.37.0 1.37.0-3ubuntu3
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe libtorrent-rasterbar2 0.14.2-2ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe python-libtorrent 0.14.2-2ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe deluge-core 1.1.6+dfsg-2ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe deluge-common 1.1.6+dfsg-2ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) jaunty/universe deluge-console 1.1.6+dfsg-2ubuntu1
  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/b/boost1.37/libboost-python1.37.0_1.37.0-3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/boost1.37/libboost-python1.37.0_1.37.0-3ubuntu3_i386.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/b/boost1.37/libboost-system1.37.0_1.37.0-3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/boost1.37/libboost-system1.37.0_1.37.0-3ubuntu3_i386.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/b/boost1.37/libboost-filesystem1.37.0_1.37.0-3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/boost1.37/libboost-filesystem1.37.0_1.37.0-3ubuntu3_i386.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/b/boost1.37/libboost-thread1.37.0_1.37.0-3ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/b/boost1.37/libboost-thread1.37.0_1.37.0-3ubuntu3_i386.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/libtorrent-rasterbar2_0.14.2-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/libtorrent-rasterbar2_0.14.2-2ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/python-libtorrent_0.14.2-2ubuntu1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/python-libtorrent_0.14.2-2ubuntu1_i386.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/d/deluge/deluge-core_1.1.6+dfsg-2ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/d/deluge/deluge-core_1.1.6+dfsg-2ubuntu1_all.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/d/deluge/deluge-common_1.1.6+dfsg-2ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/d/deluge/deluge-common_1.1.6+dfsg-2ubuntu1_all.deb)  404 Not Found [IP: 91.189.88.45 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/universe/d/deluge/deluge-console_1.1.6+dfsg-2ubuntu1_all.deb](http://archive.ubuntu.com/ubuntu/pool/universe/d/deluge/deluge-console_1.1.6+dfsg-2ubuntu1_all.deb)  404 Not Found [IP: 91.189.88.45 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
=========================================================

How can I get Transmission to 'give' me an account? I can't see how I can have an account.

---

### Post by seawolf167 on 2011-05-31
Its not Transmission that gives you an account - it is the tracker tracking the torrent. An example is [demonoid]("http://www.demonoid.me"), you cannot download torrents from there (even with the .torrent file) unless you have an account.

As for Deluge, can you install it through the Ubuntu Software Center? Search for deluge, then click install.

---

