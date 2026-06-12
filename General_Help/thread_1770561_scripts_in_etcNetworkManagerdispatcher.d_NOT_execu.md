---
title: "scripts in /etc/NetworkManager/dispatcher.d NOT executing"
date: 2011-05-29
forum: General Help
---

### Post by scopper on 2011-05-29
hey all, 

Thanks for your time. I'm trying to have a script execute when a certain network event happens. In order to first make sure networkmanager is executing scripts in dispatcher.d, I put a simple script in there, with appropriate permissions/ownership. I can execute the script from the command line without error. But when I cause the network status to change, say, by unplugging my ethernet cable, the script does not execute. I'm posting the script, and I'm happy to post anything else that may be of help.
Again this is a simplified script in order to first ensure that it will be executed...

```

#!/bin/sh -e


exec /usr/bin/wmctrl -c qBittorrent

exit 0
```


Thanks!

---

### Post by scopper on 2011-05-29
basic system info: 10.10 64bit amd3800
gnome 2.32.0

---

### Post by scopper on 2011-05-30
the script wasn't able to call 'wmcntrl' for some reason... but killall-9 qbittorrent works just fine

---

