---
title: "Startup script ..."
date: 2009-08-17
forum: General Help
---

### Post by nunyez on 2009-08-17
Alright this is really starting to piss me off now ;).  I have a simple script that starts my screen sessions on startup.  

1. Tried adding it to the noob friendly startup sessions screen, it doesn't run.
2. Tried putting it in rc.local, doesn't run.
3. Runs in /etc/init.d with defaults but attaches early in the boot process which ***** everything up. I tried specifying it to start as detached but that didn't work for me either

The most promising seems to be init.d but I am unsure which bootlevels for it to start at.  And maybe its just me but the detached part isn't working for me, it starts attached anyways.

My script, chmod'd 755 (which runs fine when I $bin/start-screen.sh): 
```

#!/bin/sh
# Start yer screens
screen -S torrent rtorrent
screen -S irssi irssi

```

---

### Post by Brandon Williams on 2009-08-17
For inclusion in a startup script, you should use both the -d flag and the -m flag, which means that the script should look like this:
```
#!/bin/sh
screen -d -m -S torrent rtorrent
screen -d -m -S irssi irssi
```

This works for me when defined as a session startup application. If that isn't working for you, then take a look in your .xsession-errors file to see if it gives you any clue as to what the problem is.

---

