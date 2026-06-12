---
title: "MPD+sonata"
date: 2010-05-01
forum: General Help
---

### Post by darkwish_ on 2010-05-01
Hello, i have read some MPD+Sonata HOWTO but they all are outdate, so they didnt help.
I just want to make Sonata play my music on mounted NTFS.
So i have:
Ubuntu 10.04
Sonata
MPD
Music on "/media/media/music" (mounted partition "media")

pls, help me with mpd.conf:
```
######################## REQUIRED PATHS ########################
music_directory                 "/var/lib/mpd/music"
playlist_directory              "/var/lib/mpd/playlists"
db_file                         "/var/lib/mpd/mpd.db"
log_file                        "/var/log/mpd/mpd.log"
error_file                      "/var/log/mpd/mpd.error"
pid_file                        "/var/run/mpd/mpd.pid"
state_file                      "/var/run/mpd/mpd.state"
```

---

