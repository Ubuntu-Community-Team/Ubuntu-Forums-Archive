---
title: "No keyboard or mouse input at login screen"
date: 2010-12-23
forum: General Help
---

### Post by Brimjob on 2010-12-23
Hi all,

I left my computer unattended this morning and it went into hibernation mode (as usual), and when I came back and powered on I had no keyboard or mouse input at the login screen.

Also, recovery mode halts at "mountall: plymouth command failed." Any ideas as to how I can get back into my system?

Thanks.

---

### Post by Brimjob on 2010-12-24
Welp, I managed to fix my own problem. I booted up a live cd and used chroot to run

```
sudo apt-get update
sudo apt-get install -f

sudo dpkg --configure -a
sudo dpkg-reconfigure plymouth
sudo dpkg-reconfigure gdm
```

And that seems to have taken care of it. Hopefully if anyone else has this problem this'll help.

---

