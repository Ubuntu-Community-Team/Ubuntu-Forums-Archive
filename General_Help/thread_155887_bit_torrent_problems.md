---
title: "bit torrent problems"
date: 2006-04-05
forum: General Help
---

### Post by gullyhole on 2006-04-05
Ok so I am having problems installing bit torrent, I went to the howto and posted my problems but no one has replyed in two days. For details on my problems if you care you can reply in that forum. It is the howto for installing bit torrent, It is named Installing bit torrent or something along those lines. Thanks to anyone who posts in there. I am having trouble finding the files. Im not sure how to enable the universe thing, and I think that is the problem.

---

### Post by karthik085 on 2006-04-06
apt-cache search libwxgtk2.4
If this does not show any result, probably the package is in a different respo.
You can see my sources.list and upgrade your sources.list (/etc/apt)
Then, do a search again.

Once you have found out the necessary packages, install them using 
apt-get install

If you are not comfortable with commands, you can use synaptic (kynaptic in kde)

I did a search and I was able to find the necessary packages.

[QUOTE=gullyhole]Ok so I am having problems installing bit torrent, I went to the howto and posted my problems but no one has replyed in two days. For details on my problems if you care you can reply in that forum. It is the howto for installing bit torrent, It is named Installing bit torrent or something along those lines. Thanks to anyone who posts in there. I am having trouble finding the files. Im not sure how to enable the universe thing, and I think that is the problem.[/QUOTE]

---

### Post by renzokuken on 2006-04-06
alternatively install bittornado (the best client IMO) and azureus through automatix

just saecrg the forums for automatix

---

### Post by Sutekh on 2006-04-06
That HOWTO you posted on is for Warty (wayyyy old Ubuntu release).  Are you using Breezy?  

Bittorrent is available through the main Breezy repository.  You don't need to do anything fancy to get it.  That universe package is not required to run Bittorrent, it's just an enhanced GUI.

Are your repositories up-to-date?  Here are some relevant links for good repositories.

[http://www.psychocats.net/ubuntu/sources.php](http://www.psychocats.net/ubuntu/sources.php)

[Ubuntu Linux - Source-o-Matic](http://www.ubuntulinux.nl/source-o-matic)

With proper Breezy repositories, installing Bittorrent/Bittornado is pie.

Bittorrent
```
sudo apt-get install bittorrent
```is all you need.  

Bittornado
```
sudo apt-get install bittornado
```

If you want the enhanced GUI then you need to enable the universe repository.  The [psychocats.net](http://www.psychocats.net/ubuntu/sources.php) link will show you how to do that.
```
sudo apt-get install bittorrent-gui
```or```
sudo apt-get install bottornado-gui
```will install the enhanced GUI's  (unneccessay IMO)

---

