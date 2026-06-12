---
title: "transmission stops internet???"
date: 2011-09-11
forum: General Help
---

### Post by soryu on 2011-09-11
when i start using transmission  my internet stops working  it doesnt disconnect just
nothing downloads or uploads the browser too. network manager icon shows  i'm connected
i disconnect then reconnect then internet works for like 5min  then it stops again.
 this happens only happens when im using transmission.
anybody have any ideas?
i tried qbittorrent samething.

---

### Post by CDNdevil on 2011-09-11
It could be that it hogging all your bandwidth with downloading whatever your after. Try limiting the upload and download speed transmission can use, that's what I have to do.

---

### Post by SoFl W on 2011-09-11
+1  My internet speeds get very slow when I use transmission, it is a band width hog.

---

### Post by CDNdevil on 2011-09-11
Put very heavy limits on the download and upload speeds, I've got usually 1kb/s upload and 500kb/s download. Usually drop it to 20kb/s download if I play online games or just turn the thing off.

---

### Post by soryu on 2011-09-12
speeds restricted, 2 bad cant go unlimited.

---

### Post by LMP900 on 2011-09-12
This thread about a similar issue has a few explanations: ([link]("http://ubuntuforums.org/showthread.php?t=1837560")) My suggestion was to update the router's firmware and others suggested Deluge instead of Transmission.

---

### Post by Vaphell on 2011-09-12
it technically can go unlimited, but the consequences are that anything-internet requires outgoing requests (yo, server, send me stuff) and it can kill them. If your torrent app eats whole upload bandwidth there is next to none left for other apps (like web browser) and everything lags out and pretty much dies. Also crappier models of routers are not really built for heavier usage and are unable to keep up with heavy load.

try 50-70% of available upload, it should leave enough room for other programs to have easy access to online resources.
also limit number of connections to 100-200 (reduces load on routers and their connection tables and overhead of continuous connection management in torrent protocol) and have only 1-2 torrents downloading at a time (they compete for bandwidth either way so there is no point in having 10 concurrent active downloads)

---

