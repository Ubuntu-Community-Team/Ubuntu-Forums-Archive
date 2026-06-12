---
title: "Can't install bittorrent"
date: 2006-04-25
forum: General Help
---

### Post by ericheadley on 2006-04-25
Tried to download a file and it said "Client version is banned. Check with tracker administrator"

Then I tried to install bittorrent with:
sudo apt-get install bittorrent

but got :

Reading package lists... Done
Building dependency tree... Done
bittorrent is already the newest version

Then I tried downloading the official bittorrent  and installing it but got : 

sudo dpkg -i BitTorrent-Stable.deb (Reading database ... 63659 files and directories currently installed.)
Unpacking bittorrent-4.4.0.linux (from BitTorrent-Stable.deb) ...
dpkg: error processing BitTorrent-Stable.deb (--install):
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Choker.py', which is also in package bittorrent
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 BitTorrent-Stable.deb

Any ideas of what I can try.  I know ther are other clients to try but why aren't these working ?

---

### Post by TmP on 2006-04-25
If you'r using Azureus, it has some options that are banned by many trackers. Try other clients.

---

### Post by ubuntu27 on 2006-04-25
[QUOTE=ericheadley]Tried to download a file and it said "Client version is banned. Check with tracker administrator"

Then I tried to install bittorrent with:
sudo apt-get install bittorrent

but got :

Reading package lists... Done
Building dependency tree... Done
bittorrent is already the newest version

Then I tried downloading the official bittorrent  and installing it but got : 

sudo dpkg -i BitTorrent-Stable.deb (Reading database ... 63659 files and directories currently installed.)
Unpacking bittorrent-4.4.0.linux (from BitTorrent-Stable.deb) ...
dpkg: error processing BitTorrent-Stable.deb (--install):
 trying to overwrite `/usr/lib/python2.4/site-packages/BitTorrent/Choker.py', which is also in package bittorrent
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 BitTorrent-Stable.deb

Any ideas of what I can try.  I know ther are other clients to try but why aren't these working ?[/QUOTE]

The "problem" is that you already have a package called "BitTorrent" I guess it is the GNOME Bittorrent.

You want to install the OFFICIAL Bittorrent?

Then, follow this steps:

First, remove your current installed Bittorrent by wirting the following command in the Terminal:

```
sudo apt-get remove bittorrent
```

Next, download the Official Bittorrent package that ends with *.deb

I jsut checked the Bittorrent website. you have to download "BitTorrent-Stable.deb"

and then in the terminal type:

```
sudo dpkg -i BitTorrent-Stable.deb 

```

and voila! Now you have Official BitTorrent Installed ;)

---

### Post by ericheadley on 2006-04-27
Thank you ubuntu27 that has worked.  Simple enough if you know how.  Once again thanks.

---

### Post by ubuntu27 on 2006-04-27
[QUOTE=ericheadley]Thank you ubuntu27 that has worked.  Simple enough if you know how.  Once again thanks.[/QUOTE]


Glad I was Able to Help You :) 


Now! Fly Free! I mean, Enjoy your Ubuntu!! :D

---

