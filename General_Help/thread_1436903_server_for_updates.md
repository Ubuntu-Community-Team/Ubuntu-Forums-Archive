---
title: "server for updates"
date: 2010-03-23
forum: General Help
---

### Post by cong06 on 2010-03-23
I have a server that has apt-cacher installed as it's local proxy. What I want to do is place this computer in a place that has good internet and copy the updates from it to a flash, periodically, and move them to a separate computer.
I could use Keryx, but I don't want to deal with graphical interfaces. I want a command line computer.

The only way I can think to do this is to have all the software installed, and have it set to automatically download and install updates.

I don't like this, because it means that my "server" has to be quite a bit more bloated then it needs to be.

Does anyone have any brilliant ideas on how to get this server to download updates for this software periodically without actually installing them?

I guess I could make a list of all the software installed:
```

dpkg --get-selections | grep -v "deinstall" | awk '{print $1}'

```
 and have my server (through it's apt-cacher proxy) continuously (like once a day) re-download:
```

aptitude download ${long_list_of_software}

```
Is that the cleanest?

---

### Post by cong06 on 2010-03-24
ok. So what I decided to settle for (please don't hesitate to post a better idea) is something like this:


/etc/cron.daily/apt_update
```

#!/bin/bash
array_with_software=(

)

aptitude update && aptitude --assume-yes --download-only ${array_with_software[@]}

```
That should take care of all dependencies, and keep everything up to date so I can grab it later when I want.

---

