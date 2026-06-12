---
title: "Moblock for kubuntu Jaunty"
date: 2009-08-15
forum: General Help
---

### Post by Shabakthanai on 2009-08-15
I installed moblock and it is working, perhaps too good.  Upload speeds are fine at between 60 and 80kpbs.  Downloads remain in a que status and nothing downloads.  By the list of things that are blocked, I suspect I have configuration problems, but I don't know what I actually need and what is not needed to download videos and the like.  I looked for beginner forums but cannot seem to find one that explains in terms I can understand.  Thank you.

---

### Post by lovinglinux on 2009-08-16
I'm assuming you are referring to torrent or other p2p download. It seems that you have too many IP ranges blocked. Try reducing the number of lists by editing **/etc/blockcontrol/blocklists.list** or from mobloquer interface.

To install mobloquer:

```
sudo apt-get install mobloquer
```

These might help.

[http://moblock-deb.sourceforge.net/](http://moblock-deb.sourceforge.net/)

[General MoBlock thread ](http://ubuntuforums.org/showthread.php?t=803183)

---

