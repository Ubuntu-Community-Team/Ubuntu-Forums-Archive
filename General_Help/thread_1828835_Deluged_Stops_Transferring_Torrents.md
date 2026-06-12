---
title: "Deluged Stops Transferring Torrents"
date: 2011-08-19
forum: General Help
---

### Post by Munk3y on 2011-08-19
I've been trying to get some help with a problem I'm having in Deluge. I started on the Deluge forums but am not really getting much help, so I figured I'd post here and see if maybe someone has an idea of what's going on.

Original post: [http://forum.deluge-torrent.org/viewtopic.php?f=7&t=37391](http://forum.deluge-torrent.org/viewtopic.php?f=7&t=37391)

Everything's in that thread but a quick recap:

OS: Ubuntu 11.04 (Completely up to date)
Libtorrent: 0.15.6.0 (From PPA)
Deluge: 1.3.3 (From PPA)

I'm running Deluged and using the Web Interface. I start the computer up and download the first Torrent (or set of Torrents) fine. After they're done, if I add any more Torrents then it won't transfer them at all. It shows no Seeders. Peers go up and down like they're trying to connect but losing connection. 20-45 minutes later, it starts downloading. Until I updated to the PPA version, it would download slowly but after updating now it downloads full speed. If I kill Deluged (Rather than waiting a possible 45+ min for it to start) then it starts downloading at full speed right away.

Screenshots of my config and a Debug log are in the thread listed above. If anyone has some suggestion, I would be very grateful. If there's any more information I can provide, please let me know.

---

### Post by zensawa on 2011-08-19
Use transmission, dont forget to goto preferences and click require encryption, stupid thing dosent work as good without the required encryption thing. :popcorn:

---

### Post by Munk3y on 2011-08-19
Thanks. Other Torrent clients do work fine and don't have this problem but it's a headless box that I access from across the network and so I use the Web Interface. I've looked around for some clients that have a Web Interface to replace it but haven't found anything as nice.

---

### Post by Munk3y on 2011-08-19
I think I might try Transmission's Remote GUI, that seems kind of cool. Been using Deluge forever but oh well.

---

### Post by jfed on 2011-08-19
I always had problems with the Web UI. The biggest of which is that it only runs in Firefox, not Chrome. 

Try using an FTP client like Filezilla and transferring the files into Deluge>Torrents>Autoload thats what I do, because for some reason I could just never get the Web UI to work properly.

---

