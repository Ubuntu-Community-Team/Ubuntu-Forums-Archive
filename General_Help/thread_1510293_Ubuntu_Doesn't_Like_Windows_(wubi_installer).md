---
title: "Ubuntu Doesn't Like Windows (wubi installer)"
date: 2010-06-15
forum: General Help
---

### Post by I like cheese biscuits on 2010-06-15
Using wubi installer in safe mode to install Ubuntu on my new computer, (I have Windows 7 and computer is two months old), It gets to about half way downloading the torrent and then comes up with something telling me it has been denied access.

I have full administrator access, my PC is working fine, this has happened ten times already. Does anyone have a solution that doesn't require a CD or EPIC instructions to making sure wubi can download the torrent and install Ubuntu without Windows freaking out?

---

### Post by WorMzy on 2010-06-15
The torrent stops? Then you have a problem with the program you're using to download the torrent. [Try a different client]("http://en.wikipedia.org/wiki/Comparison_of_BitTorrent_clients#Operating_system_support").

---

### Post by warfacegod on 2010-06-15
FYI: Wubi isn't really meant as a permanent install but more as a way to try Ubuntu. It's easily broken by kernel updates. Among other things.

If you really want to install Ubuntu, go into 7 and defrag, use 7's Disk Manager to resize 7, run Windows chdsk, boot into a LiveCD/USB and use Gparted to create a small ext4 partition for Ubuntu and a larger one for your /home, install, run Windows chdsk again.

---

