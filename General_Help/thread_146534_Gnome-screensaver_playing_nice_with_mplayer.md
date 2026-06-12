---
title: "Gnome-screensaver playing nice with mplayer"
date: 2006-03-18
forum: General Help
---

### Post by markballermann on 2006-03-18
This is a workaround to prevent gnome-screensaver from starting while mplayer is running. I wrote a little script to kill the screensaver, then start mplayer, then restart the screensaver when mplayer is done. Put this script somewhere:

```

#!/bin/bash
killall gnome-screensaver
mplayer "$1"
gnome-screensaver&

```
I called it ~/.scripts/gnome-mplayer
Make it executeable with
```

chmod a+x ~/.scripts/gnome-mplayer

```

Then in nautilus, right click on a movie file and go to 'properties' then 'open with' then use a custom command pointing to the script, and set it as default.

I'd use xscreensaver instead of gnome-screensaver, but I found it crashes mplayer when paused and 'xscreensaver-disable' is used. 

Hopefully this is helpful.

---

### Post by hyperair on 2007-11-12
Rather useful. Thanks. ^^ I totally didn't think of that. It is a bit hackish though.

---

