---
title: "Little notifyosd helper for rtorrent"
date: 2010-02-10
forum: General Help
---

### Post by ridetheteapot on 2010-02-10
Hey i was just fiddling around with my new laptop making stuff look pretty --- and i was thinking i should have ubuntu's notify osd alert me when torrents finish.
It's real easy. you just need the package libnotify-bin for notify-send

add this to your .rtorrentrc (think this apllies to rtorrent>8.4)
```

system.method.set_key = event.download.finished,notify_me,"execute=~/bin/rtorrent_notify.sh,$d.get_name="

```

then make the file ~/bin/rtorrent_notify.sh and and this
```

#!/bin/sh
notify-send "Torrent Finished!" "$1"

```
note that this is really simple; the advantage of using a script instead of just doing this in .rtorrentrc is that you can add any other options here easily like email alerts or whatever. also notify-send accepts icons with the -i switch (check the man page for default icon set)


don't forget to make this executable.

i dont really post howto's but this was just an easy essential addition to rtorrent. if it interests anyone i have a few things for rtorrent as far as auto screen resume and launching suggestions.

---

