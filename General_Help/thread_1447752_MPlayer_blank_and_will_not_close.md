---
title: "MPlayer blank and will not close"
date: 2010-04-05
forum: General Help
---

### Post by toyoracer on 2010-04-05
Good day. I opened MPlayer, two boxes opened, both a blank and will not close. System manager does not show it and "ALT-F2" typed xkill and clicked on bottom tray button does nothing. I opened second MPlayer and it closed but not first one. Any suggestions thanks.

---

### Post by NT4usB on 2010-04-05
Is it mplayer or gmplayer that's running?
Open a terminal and type:
```
ps aux | grep mplayer
```Then:```
killall mplayer
```or:```
killall -9 mplayer
```The last one, I have to use when a .mkv hangs at the end and no amount of killing kills it.
Substitute gmplayer if that's what's running/hung.

---

### Post by toyoracer on 2010-04-05
Thank you that worked. I opened the wrong one wanted Rhythmbox and MPlayer would not close, who knows. Thanks again.

---

