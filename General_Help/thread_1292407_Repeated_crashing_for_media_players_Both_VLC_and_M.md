---
title: "Repeated crashing for media players: Both VLC and MPlayer"
date: 2009-10-15
forum: General Help
---

### Post by FroogleDoop on 2009-10-15
When I play ANY sort of media on either VLC of MPlayer, there is (without exception) a 50/50 chance that one of them will crash/freeze up. This happens no matter what I'm watching; be it a movie or a 26-minute show. Has anyone ever had this problem/does anyone have any idea what might be causing this? It is beyond me.

---

### Post by P4man on 2009-10-16
launch them from a terminal, so at least you can see some errors if/when it crashes

---

### Post by frontrow on 2009-10-17
try this:

open a terminal
type "gstreamer-properties"

Multimedia System Selector window opens

select the video tab

set the default video plug in to X Window System (No Xv)

close

try 'er now.

---

