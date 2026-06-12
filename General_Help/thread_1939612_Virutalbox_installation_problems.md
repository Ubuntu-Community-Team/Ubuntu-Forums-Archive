---
title: "Virutalbox installation problems"
date: 2012-03-12
forum: General Help
---

### Post by sekhar.rahul on 2012-03-12
I'm running Ubuntu 11.10 with kernel 3.3rc6. I tried to install Virtualbox 4.1.8 with the AMD64 .deb package off the virtualbox site. On install I got a kernel panic saying "unable to handle kernel paging request at ffff...".

When I try to boot into Ubuntu now, it starts to run unattended upgrades and I again get:

```
* Starting VirtualBox kernel modules
unable to handle kernel paging request at ffff...
...etc
```

I booted up okay on recovery mode, but when I shut down the system it gets stuck on:

```
* Stopping VirtualBox kernel modules
```

and I have to manually power down.

If I try ```
sudo apt-get remove virtualbox-4.1
``` it similarly gets stuck while stopping the virtualbox kernel modules.

At the moment I'd be happy just removing the problematic install so my system boots up okay. I don't really need virtualbox right now, but I do need a working system. Any help would be much appreciated. Thanks!

---

### Post by sekhar.rahul on 2012-03-12
I managed to sort this out very crudely. I renamed /etc/init.d/vboxdrv to vboxdrv.bak so that the Virtualbox kernel module service would not start (and hence not get stuck while stopping.)

I then rebooted and did a sudo apt-get remove --purge virtualbox-4.1, which worked fine.

I'm sure there's a more elegant way to do this. Anyway, I'm glad I no longer have the issue. Apologies for the unnecessary thread - can it be closed/moved/whatever?

---

