---
title: "Howto - Shutdown When Idle - 10.04"
date: 2010-10-07
forum: General Help
---

### Post by slipdipper on 2010-10-07
I was looking for an easy way to do this, but apparently gnome's pwr mgmt options dont let you shut the system down after it becomes idle. Here's one work around, let me know if you have a better way


Create a new script to make stuff work
```
sudo touch /etc/pm/sleep.d/10_shutdown
```

become root, then fill it with goodies :
```

#!/bin/bash

. /usr/lib/pm-utils/functions

case "$1" in
    hibernate|suspend)
    shutdown -h now
    ;;
    *)
    ;;
esac

```

Set it to be executable
```
sudo chmod +x /etc/pm/sleep.d/10_shutdown
```

---

### Post by nwalkey on 2012-11-15
Can you explain how this script works for me? Do you know of a way to get the computer to reboot after being idle for a set period of time?

---

### Post by wildmanne39 on 2012-11-15
If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.

---

