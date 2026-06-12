---
title: "Spotify Now Playing Script"
date: 2011-05-15
forum: General Help
---

### Post by gamer_boy on 2011-05-15
Hi all,

Does anyone have a working Conky config with a Spotify now playing script? I have found the following ```
#!/bin/sh
pgrep spotify 1>/dev/null 2>&1
if [ $? != 0 ]; then
  exit 1
fi

xwininfo -root -tree | grep '"Spotify": ("spotify" "Spotify")' 1>/dev/null 2>&1
if [ $? != 0 ]; then
  xwininfo -root -tree | grep -m 1 '("spotify" "Spotify")' | grep -v 'has no name' | sed 's/[ ]*0x[0-9a    -f]* "Spotify - \(.*\)": ("spotify" "Spotify").*/\1/'
else
  exit 1
fi

```

and I understand the principle but I can't get it to work. This seems to rely on the now playing window of Spotify being the first entry on the processes list to do with Spotify. Any ideas?

Cheers,
James

---

### Post by milouse1664 on 2011-11-04
Hello,

With the new version of spotify for linux (>= 0.4.8) you can control it with dbus. So your now-playing script should look as the following:

```
#!/bin/bash

echo `dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get string:'org.mpris.MediaPlayer2.Player' string:'Metadata'|egrep -A 2 "artist"|egrep -v "artist"|egrep -v "array"|cut -b 27-|cut -d '"' -f 1|egrep -v ^$` "-" `dbus-send --print-reply --dest=org.mpris.MediaPlayer2.spotify /org/mpris/MediaPlayer2 org.freedesktop.DBus.Properties.Get string:'org.mpris.MediaPlayer2.Player' string:'Metadata'|egrep -A 1 "title"|egrep -v "title"|cut -b 44-|cut -d '"' -f 1|egrep -v ^$`

```

Cheers

---

