---
title: "BT clients that support hex magnet links?"
date: 2009-11-19
forum: General Help
---

### Post by gilgongo on 2009-11-19
Now that everyone in the world (well, mostly everyone) wants to use BitTorrent without a tracker, does anyone know which BT clients in the repos support magnet links in hex format?

The ones I've tried (Azureus and the one that comes by default in Karmic) don't.

---

### Post by XCan on 2009-11-19
Edit: Misunderstood question.

---

### Post by KIAaze on 2009-11-19
Azureus/Vuze 4.3.0.1 beta does.

Related thread: [http://ubuntuforums.org/showthread.php?t=1273985](http://ubuntuforums.org/showthread.php?t=1273985)

You can easily convert hex links into base 32 by using this base converter:
[http://darkfader.net/toolbox/convert/](http://darkfader.net/toolbox/convert/)

Convert from "hexadecimal 0-9A-Za-z" to "base 32 A-Z2-7". ;)

ex:
```
Original hex link:
magnet:?xt=urn:btih:24ec1f97b8288b15943096278dcf11c4487416e0&dn=US_NOW-720.mp4&tr=http://tracker.openbittorrent.com/announce

Hex number to convert:
24ec1f97b8288b15943096278dcf11c4487416e0

Upper-case (online-converter only seems to accept uppercase):
24EC1F97B8288B15943096278DCF11C4487416E0

Base 32 result:
ETWB7F5YFCFRLFBQSYTY3TYRYREHIFXA

Corresponding base 32 magnet link:
magnet:?xt=urn:btih:ETWB7F5YFCFRLFBQSYTY3TYRYREHIFXA

You can add the display name (dn) if you want:
magnet:?xt=urn:btih:ETWB7F5YFCFRLFBQSYTY3TYRYREHIFXA&dn=US_NOW-720.mp4&tr=http://tracker.openbittorrent.com/announce

```

---

### Post by KIAaze on 2009-11-19
I wrote a litte script to convert magnet links: [http://ubuntuforums.org/showpost.php?p=8348910&postcount=29](http://ubuntuforums.org/showpost.php?p=8348910&postcount=29)

---

### Post by fluffman86 on 2009-11-19
Sites still offer .torrent files, which are useful for using DHT even if the client can't accept magnet links directly.  That said, Vuze takes magnet, deluge will take it from the command line (check out the bittorent threads on the next page), and transmission is working on it.

---

### Post by gilgongo on 2009-11-19
OK thanks all - seems like there's hope at least until the new version of Vuze, and others, get into the repos.

---

