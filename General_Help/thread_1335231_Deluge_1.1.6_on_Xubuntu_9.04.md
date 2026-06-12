---
title: "Deluge 1.1.6 on Xubuntu 9.04"
date: 2009-11-23
forum: General Help
---

### Post by scott1981ar on 2009-11-23
Hi All,

I installed Xubuntu 9.04 yesterday and installed Deluge mainly because I use it on another machine and it allows you to control it remotely through the web GUI. However it seems that the newer version (1.1.6) does not have the plugin installed as the old one did by default. Do you know what package I should install in order to allow web management? (I already tried deluge-web and deluge-webgui and none of those seem to exist).

Thanks.

---

### Post by Cas07 on 2009-12-07
I'm new to Deluge but i installed 1.2.0rc4 without any issues on Karmic. I used the PPA packages from here:
[https://launchpad.net/~deluge-team/+archive/ppa](https://launchpad.net/~deluge-team/+archive/ppa)

Documentation is a bit thin in places but this is my take on the packages needing installed:

[INDENT]The daemon server **deluged ** is the core of deluge and the following are the clients that connect to the server and provide your different interfaces of gui, console and web:
**deluge-gtk** - GTK GUI client
**deluge-web** - web server
**deluge-console** - console client[/INDENT]

For startup init i used this guide:
[http://dev.deluge-torrent.org/wiki/UserGuide/InitScript](http://dev.deluge-torrent.org/wiki/UserGuide/InitScript)

Hope this helps

---

