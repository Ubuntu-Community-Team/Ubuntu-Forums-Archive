---
title: "&quot;couldn't open audio&quot; dialog"
date: 2006-04-30
forum: General Help
---

### Post by lonelypauly on 2006-04-30
whenever i stop audio in xmms and use another app like rythymbox or streamtuner my audio no longer plays and i get this message...

[IMG]http://i6.photobucket.com/albums/y215/lonelypauly/audio.jpg[/IMG]

any ideas?

---

### Post by hollywoodb on 2006-04-30
Could be ESD.  To disable ESD:

System -> Preferences -> Multimedia Systems Selector
change it to ALSA instead of ESD.

Sysem -> Preferences -> Sound Preferences
uncheck 'Enable sound server startup'

in a terminal:
"killall esd"

In your apps select audio output as ALSA, or gstreamer ALSA output, or Xine ALSA output, depending on the app.  If this doesn't help you can reverse the process by reversing the 1st two steps above.

---

