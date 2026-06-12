---
title: "Window freeze issue in mirror and span monitor mode with compiz on ?"
date: 2011-09-27
forum: General Help
---

### Post by excetara2 on 2011-09-27
The window freezes and causes this to occur as the pictures below where the screen freezes. Then it remembers everything that was at that location on the background of the screen. Is there a way to reset this? It has happened before but automatically went back to normal after a bit of fiddling. I can't remember what I had done to fix fix. 1) Is there a way to clear what monitors it remembers so it thinks its a new monitor?? 2) Or just resetting compiz without losing my settings though.

Or up for any ideas. Let me know.

[[IMG]http://img220.imageshack.us/img220/8442/screenshot1aq.th.png[/IMG]](http://imageshack.us/photo/my-images/220/screenshot1aq.png/)

---

### Post by excetara2 on 2011-09-27
Seemed to fix it by booting into failsafe gnome and then running:

rm -r .compiz

which all that was in that folder was a bunch of session information. I'm not sure if it was required or just booting into failsafe gnome and then back would do the trick. It seemed to fix it either way.

---

