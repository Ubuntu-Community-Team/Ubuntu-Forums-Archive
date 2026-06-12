---
title: "Startup Script"
date: 2009-06-25
forum: General Help
---

### Post by Sonthun on 2009-06-25
I'm trying to run a startup script that will restart the mythbackend after my hdhomerun is detected.  The script itself works, but I can't seem to get it to run at startup.  I put a simple test command of "gnome-terminal" so that I will know if it runs it it opens up a terminal.  I used```
sudo update-rc.d -f mythbackendrestart.sh defaults
``` to get in to the startup rotation and then changed the start level to 98 so that it will execute after everything else.  Why isn't it running at startup?

Thanks.

---

