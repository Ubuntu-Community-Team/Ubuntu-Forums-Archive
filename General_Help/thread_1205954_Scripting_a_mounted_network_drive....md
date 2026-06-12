---
title: "Scripting a mounted network drive..."
date: 2009-07-06
forum: General Help
---

### Post by fluidbyte on 2009-07-06
Relatively new to *nix, and I've been working on mounting network shares on my Windows network. I wrote a script that seems to work:
```

#!/bin/bash
sudo /sbin/mount.cifs //myserver/share /media/share

```I am having two issues (perhaps 1 will fix the other):

1.  When I run the script it brings up the terminal and requires me to enter my password.
2. I can't get it to run on startup (yes - I tried System >> Preferences >> Startup Applications, and linking to the script).

Any help would be greatly appreciated.

Also - is there a way I could add multiple shares to this? I tried adding another line and it didn't seem to work... may be my lack of scripting experience.

---

