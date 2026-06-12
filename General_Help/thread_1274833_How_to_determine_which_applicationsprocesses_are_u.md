---
title: "How to determine which applications/processes are using my bandwidth?"
date: 2009-09-25
forum: General Help
---

### Post by rob86 on 2009-09-25
I'm on a dialup, so when something's using all my bandwidth in the background, I'd like to know what it is so I can shut it off. I had this problem a few minutes ago, Something was downloading, Firestarter showed dozens of strange IP with strange ports. I figured it was Transmission torrent downloader running in the background, but I looked in system monitor and it wasn't going. I have no idea what was doing it, but I rebooted and it went away.

Anyway, back to the main question, is there any way to find out what's using my bandwidth? Some built in command or an app to download? 

Netstat didn't really work that great. It showed two connections and neither were suspicious, yet there was something downloading.

---

### Post by mikewhatever on 2009-09-25
Could have been the update manager updating its package information. You can disable it and run manually once a week or so. Nothing else should be accessing the net in the background by default.

---

