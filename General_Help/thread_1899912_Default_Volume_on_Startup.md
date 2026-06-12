---
title: "Default Volume on Startup"
date: 2011-12-24
forum: General Help
---

### Post by Spectre5 on 2011-12-24
I'm trying to setup a few things on a new computer.  Every time I restart the computer, the output volume is very low (maybe 20%).  I have to adjust it back up to 100%.  It stays at 100% and works perfect, until I restart again.  How can I fix this?

I tried this (from another thread, don't have the link handy), but it didn't work (do it after setting the volume to what you want):
```
sudo alsactl store 0
```

Any other suggestions?  I'm running Ubuntu 11.10.  Thanks!

---

### Post by stinkeye on 2011-12-24
This works for my internal sound card.
```
pacmd set-sink-volume [COLOR="Red"]1[/COLOR] [COLOR="DarkOrchid"]66666[/COLOR]
```
[COLOR="red"]Sink[/COLOR]... eg internal sound card.
Using [COLOR="Red"]0[/COLOR] changes the headset volume.
[COLOR="darkorchid"]Sets to 100%[/COLOR].


This  is from a script I downloaded to toggle between speakers and usb headset.
It lists my sinks.
```
pacmd list-sinks | sed -n -e 's/\**[[:space:]]index:[[:space:]]\([[:digit:]]\)/\1/p'
```

If you open up sound preferences at the output tab you will see if the first command works.

---

### Post by Spectre5 on 2011-12-25
That second command only had one output (0).  Trying 1 in the first command gives the message: "No sink found by this name or index."  If I use 0, it works correctly and set the volume to 100% with that first command.

However, it still gets set back to being very low when I restart the computer :(

Any other suggestions?

---

### Post by stinkeye on 2011-12-25
Make a script and put it in to startup applications.
Make the script executable.
```
#!/bin/bash

sleep 5 
pacmd set-sink-volume 0 66666
```

---

