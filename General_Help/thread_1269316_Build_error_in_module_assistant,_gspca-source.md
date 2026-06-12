---
title: "Build error in module assistant, gspca-source"
date: 2009-09-18
forum: General Help
---

### Post by Zoey.Marie on 2009-09-18
Ok... so I would post what the build log thingie says, but I don't know how to select all the text (select all selects the sreen, and pastes only the screenshot of the log file viewer... o.O) 

I have a logitech web cam. I figured out that I need to install some gspca drivers... I downloaded the tar.gz file, but I didn't really know how to install it.
-- I checked the synaptic, and they had it! gspca-source, so I figured I could just check it (and all it's dependencies) and then hit apply. Then I had to use module assistant to make the actual file and whatnot.

I did

  $ m-a prepare
  $ m-a a-i gspca

And then it told me there was an error in building it.

Any help please?

---

### Post by Zoey.Marie on 2009-09-18
someone from irc helped me figure it out...

---

### Post by Hazmy on 2011-05-07
> **Zoey.Marie said:**
> someone from irc helped me figure it out...

So post a solution ! :D

---

### Post by no2498 on 2011-05-07
Hazmy plug your cam in
open a terminal type dmesg click enter
after it stops type lsusb click enter
that should give a number and name of your cam in case you need a driver
most all cam drivers are in the kernel now days

in the terminal type gstreamer-properties click enter

click video
try v4l and v4l2
use the bottom test button for each 1
you may need to change the plugin to auto find your cam

install cheese try the cam in cheese

---

