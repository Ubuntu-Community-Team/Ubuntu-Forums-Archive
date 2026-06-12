---
title: "How to write Shell Script to change Resolution"
date: 2010-08-06
forum: General Help
---

### Post by brain!ac on 2010-08-06
Hi all

I need help on writing a Shell script which changes my X11.org config to 800x600 from any other resolution .

Best on advance

---

### Post by inameiname on 2010-08-06
Not sure if this will help you at all, but this is what I've used to change my resolution temporarily, as in when I want to watch something from the computer on an older tv that isn't digital:

```

#!/bin/bash

xrandr --addmode S-video 800x600
xrandr --output S-video --mode 800x600
xvattr -a XV_CRTC -v 1
xrandr --output VGA-0 --mode 800x600 --output S-video --mode 800x600 --same-as VGA-0

```...and then, to turn it back to before:

```

#!/bin/bash

xrandr --output VGA-0 --mode 1024x768 --output S-video --mode 800x600 --same-as VGA-0
xvattr -a XV_CRTC -v 0
xrandr --output S-video --off

```...however, while this worked well under Karmic, in Lucid the latter of the two scripts doesn't seem to work. (The first still works, though.) I haven't used it that much to warrant an attempt to fix it.

Perhaps you can tweak these or something...

---

