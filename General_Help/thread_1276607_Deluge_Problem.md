---
title: "Deluge Problem"
date: 2009-09-27
forum: General Help
---

### Post by lenswipe on 2009-09-27
Hey guys


Today i went to try and launch deluge torrent client and it refused to open so i ran "deulge" from terminal and here is the output:

( i ran deluge > textfile.txt) to write the output to a text file


```

no existing Deluge session
Starting new Deluge session...
deluge_core; using libtorrent 0.13.0.0. Compiled with NDEBUG.
Applying preferences
save uploaded memory
Pickling state...
Scanning plugin dir /usr/share/deluge/plugins
Initialising plugin SpeedLimiter
Initialising plugin TorrentCreator
Initialising plugin BlocklistImport
Initialising plugin NetworkGraph
Initialising plugin Search
Initialising plugin Scheduler
Initialising plugin TorrentFiles
Initialising plugin WebSeed
Initialising plugin EventLogging
Initialising plugin TorrentNotification
Initialising plugin NetworkHealth
Initialising plugin MoveTorrent
Initialising plugin DesiredRatio
Initialising plugin FlexRSS
Initialising plugin TorrentPeers
Initialising plugin WebUi
Applying preferences
Starting DHT...
No DHT file to resume

```


Anyone have any thoughts on that?


-Lenswipe

---

### Post by chayzer on 2009-10-15
If you want to wipe all settings and start from a fresh deluge, you could just type in

```
rm -r ~/.config/deluge 
```

just keep in mind there's no going back after that.

---

