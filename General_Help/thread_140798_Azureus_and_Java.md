---
title: "Azureus and Java"
date: 2006-03-06
forum: General Help
---

### Post by moffa on 2006-03-06
When I try running java, it takes about 2-3 minutes to load and I keep getting the following error in the console:

DEBUG::Mon Mar 06 23:44:38 EST 2006
  java.lang.NullPointerException
        at org.gudy.azureus2.ui.swt.StartServer.pollForConnectionsSupport(StartServer.java:99)
        at org.gudy.azureus2.ui.swt.StartServer.access$000(StartServer.java:28)
        at org.gudy.azureus2.ui.swt.StartServer$2.runSupport(StartServer.java:82)
        at org.gudy.azureus2.core3.util.AEThread.run(AEThread.java:64)

Any ideas?

edit: I manually installed and setup java with update-alternative, works fine after clearing all the .java folders in ~/

---

### Post by xerxesdaphat on 2006-03-21
I too have the identical problem - but I have no .java folder in my home directory. I have been running Sun's java (1.5 update 6) since I started using Azureus. Interestingly, it ran perfectly the first few times I used it (Azureus), but now it is doing strange things, the exact same to what is listed above. Can anybody help? Thank-you.

EDIT: I do have a .java folder in my home directory (was logged on as another user, how silly), however, deleting it makes absolutely no difference. I used update-alternatives to set my java environment initially and I checked it again but it is definitely using Sun's distribution.

---

### Post by moffa on 2006-03-24
I gave up on Azureus and am using Ktorrent.  If you don't like KTorrent you can also use Bittorrent or ABC.

---

### Post by xerxesdaphat on 2006-03-24
Ah but I need UPnP. And the standard BitTorrent client (v4 has UPnP) just isn't workable with the lack of features.

I've reinstalled Ubuntu from scratch anyhow and that fixed it. But it still is a confusing error, and users shouldn't have to reinstall their OS to fix it.

Thanks.

---

### Post by Dullin on 2006-03-24
Well Ktorrent does have UPnP available... just wanted to point that out.

---

### Post by xerxesdaphat on 2006-03-24
Ah really? Thanks for that, I'll have to check it out if I have problems with Azureus again. I am rather partial to Az because of its huge amount of plugins (and I'd prefer not to run KDE apps on my Gnome desktop because it's just plain ugly hahaha) but I will check it out to see if it fulfills my needs. Thanks for that info.

---

### Post by Jucato on 2006-03-24
Just be sure to download the latest KTorrent .deb release (release 1.2) from the KTorrent site. It's the one that has the plugins, including UPnP. 
Here's the download page link: [http://ktorrent.pwsp.net/index.php?page=downloads](http://ktorrent.pwsp.net/index.php?page=downloads)
They were kind enough to actually have Kubuntu debs. :D

---

### Post by f1dave on 2006-03-24
Bah, azureus. I've given up on that and my RAM's thanked me ever since.

ktorrent++

---

