---
title: "FlexGet setup troubles"
date: 2011-01-21
forum: General Help
---

### Post by chozoboy on 2011-01-21
I'm trying to set up Transmission/Deluge to do RSS feed downloading. I've got the clients working when I drop a torrent into the folder just fine, but FlexGet is giving me some trouble.
I'm using feeds from EZTV & EZRSS to get the torrents for a show. I've used the feeds for months for uTorrent in Windows, so I know they're good.

Below is my ~/.flexget/config.yml file.

```
feeds:
  The Daily Show:
    rss: 'https://www.ezrss.it/search/index.php?show_name=The+Daily+Show&date=&quality=&release_group=&mode=rss'
    series:
      - The Daily Show
    download: ~/Dropbox/Torrents/
```

flexget --check passes it, and flexget -v --test says that it would download the torrents. When I run flexget -v I get
```
2011-01-21 21:06 INFO     download      The Daily Show  Downloading: The Daily Show 2011-01-17 [HDTV - FQM]
2011-01-21 21:07 WARNING  download      The Daily Show  Could not retrieve url: http://torrent.zoink.it/The.Daily.Show.2011.01.17.%28HDTV-FQM%29%5BVTV%5D.torrent
2011-01-21 21:07 WARNING  download      The Daily Show  URLError Could not retrieve url after 3 retries.
2011-01-21 21:07 ERROR    feed          The Daily Show  Failed The Daily Show 2011-01-17 [HDTV - FQM] (URL Error)
+ download download     Failed The Daily Show 2011-01-17 [HDTV - FQM] (URL Error)

```

This happens for every torrent in the feed. I think it has something to do with it substituting %28 for [, %29 for ], and so on, but I'm not sure how to fix it (or if it's actually the problem).

Also, once that is working, how do I go about adding a second show?

---

### Post by theshrike on 2011-01-23
Try opening the torrent URL directly on the same computer that's running FlexGet, use curl, wget or something. 

Most likely zoink.it is being blocked by your ISP.

---

### Post by chozoboy on 2011-01-23
Yeah, after IRCing with on the FlexGet channel, it is trouble on zoink's side. I've switched to a bt-chat feed and it works fine.

---

